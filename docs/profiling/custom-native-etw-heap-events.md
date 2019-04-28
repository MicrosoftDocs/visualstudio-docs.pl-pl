---
title: Zdarzenia niestandardowe ETW natywnej sterty | Dokumentacja firmy Microsoft
ms.date: 02/24/2017
ms.topic: conceptual
ms.assetid: 668a6603-5082-4c78-98e6-f3dc871aa55b
author: mikejo5000
ms.author: mikejo
manager: jillfra
dev_langs:
- C++
ms.workload:
- cplusplus
ms.openlocfilehash: 1bb6f906cbfb715d67f6e10ddcecf094bc25821f
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62552964"
---
# <a name="custom-native-etw-heap-events"></a>Niestandardowe zdarzenia ETW sterty natywnej

Program Visual Studio zawiera szereg [profilowania i narzędzia diagnostyczne](../profiling/profiling-feature-tour.md), łącznie z profilera pamięci natywnej.  Przechwytuje ten program profilujący [zdarzenia ETW](/windows-hardware/drivers/devtest/event-tracing-for-windows--etw-) od dostawcy sterty i umożliwia analizowanie jak pamięci są przydzielone i używane.  Domyślnie to narzędzie tylko analizować przydziałów wykonanych ze standardowego stosu Windows i nie będzie można wyświetlić alokacje poza tym sterty natywnej.

Istnieje wiele przypadków, w których warto używać własnych niestandardowych sterty i uniknąć obciążenie alokacji ze standardowego stosu.  Na przykład można użyć [VirtualAlloc](/windows/desktop/api/memoryapi/nf-memoryapi-virtualalloc) do przydzielania dużej ilości pamięci na początku aplikację lub grę, a następnie Zarządzaj własne bloki w ramach tej listy.  W tym scenariuszu narzędzie memory profiler widział tylko tej początkowej alokacji i nie niestandardowych zarządzania wykonywane wewnątrz fragmentu pamięci.  Jednak przy użyciu dostawcy funkcji ETW sterty natywnej niestandardowego, można pozwolić narzędzie wiedzieć o dowolnych alokacji, które wykonujesz poza standardowe sterty.

Na przykład w projekcie podobnie do poniższego gdzie `MemoryPool` niestandardowe sterty jest pojedynczą alokację byłaby widoczna tylko na stosie Windows:

```cpp
class Foo
{
public:
    int x, y;
};

...

// MemoryPool is a custom managed heap, which allocates 8192 bytes
// on the standard Windows Heap named "Windows NT"
MemoryPool<Foo, 8192> mPool;

// the "allocate" method requests memory from the pool created above
// and is cast to an object of type Foo, shown above
Foo* pFoo1 = (Foo*)mPool.allocate();
Foo* pFoo2 = (Foo*)mPool.allocate();
Foo* pFoo3 = (Foo*)mPool.allocate();
```

Migawka [użycie pamięci](../profiling/memory-usage.md) narzędzia bez sterty niestandardowe śledzenia będą wyświetlane tylko alokacji jednobajtowych 8192 i żaden dokonywane przez pulę przydziały niestandardowe:

![Alokacja sterty dla Windows](media/heap-example-windows-heap.png)

Wykonując poniższe kroki, możemy użyć tego samego narzędzia do śledzenia usgae pamięci w naszym niestandardowe sterty.

## <a name="how-to-use"></a>Sposób użycia

Ta biblioteka może bez problemów używany w językach C i C++.

1. Należy dołączyć nagłówek dla dostawcy ETW sterty niestandardowe:

   ```cpp
   #include <VSCustomNativeHeapEtwProvider.h>
   ```

1. Dodaj `__declspec(allocator)` dekoratora żadnych funkcji w Menedżerze swoje niestandardowe sterty, która zwraca wskaźnik do nowo przydzielonego stosu pamięci.  Tego dekoratora umożliwia narzędzia prawidłowo identyfikować typ pamięci są zwracane.  Na przykład:

   ```cpp
   __declspec(allocator) void *MyMalloc(size_t size);
   ```

   > [!NOTE]
   > Tego dekoratora poinformuje kompilator, że ta funkcja jest wywołaniem alokatora.  Każde wywołanie funkcji zwróci adres miejsca wywołania, rozmiar instrukcji wywołania i typeId nowy obiekt do nowego `S_HEAPALLOCSITE` symboli.  Gdy stos wywołań jest przydzielany, Windows będzie emitować zdarzenia ETW za pomocą tych informacji.  Narzędzie memory profiler przedstawia stos wywołań wyszukiwania pasującego adres zwrotny `S_HEAPALLOCSITE` symboli i typeId informacje zawarte w symbolu jest używana do wyświetlania typ środowiska uruchomieniowego alokacji.
   >
   > Krótko mówiąc, oznacza to, że wywołanie, który wygląda jak `(B*)(A*)MyMalloc(sizeof(B))` pojawią się w narzędziu jako typu `B`, a nie `void` lub `A`.

1. Dla języka C++, należy utworzyć `VSHeapTracker::CHeapTracker` obiektu, podając nazwę na stosie, w którym będą widoczne w narzędziu profilowania:

   ```cpp
   auto pHeapTracker = std::make_unique<VSHeapTracker::CHeapTracker>("MyCustomHeap");
   ```

   Jeśli używasz języka C, należy użyć `OpenHeapTracker` zamiast tego funkcji.  Ta funkcja zwraca uchwyt, który będzie używany podczas wywoływania innych funkcji śledzenia:

   ```C
   VSHeapTrackerHandle hHeapTracker = OpenHeapTracker("MyHeap");
   ```

1. Podczas przydzielania pamięci przy użyciu niestandardowych funkcji, należy wywołać `AllocateEvent` (C++) lub `VSHeapTrackerAllocateEvent` metody (C), przekazując we wskaźniku do pamięci oraz ich rozmiar, aby śledzić przydział:

   ```cpp
   pHeapTracker->AllocateEvent(memPtr, size);
   ```

   lub

   ```C
   VSHeapTrackerAllocateEvent(hHeapTracker, memPtr, size);
   ```

   > [!IMPORTANT]
   > Nie zapomnij tag funkcji za pomocą niestandardowego zarządcy `__declspec(allocator)` dekoratora wcześniejszym opisem.

1. Gdy Trwa cofanie alokacji pamięci za pomocą funkcji niestandardowych, należy wywołać `DeallocateEvent` (C++) lub `VSHeapTracerDeallocateEvent` — funkcja (C), przekazując we wskaźniku do pamięci, aby śledzić dezalokację:

   ```cpp
   pHeapTracker->DeallocateEvent(memPtr);
   ```

   lub:

   ```C
   VSHeapTrackerDeallocateEvent(hHeapTracker, memPtr);
   ```

1. Gdy ponowne przydzielanie pamięci przy użyciu niestandardowych funkcji, należy wywołać `ReallocateEvent` (C++) lub `VSHeapReallocateEvent` metody (C), przekazując wskaźnik do nowej pamięci, rozmiar alokacji i wskaźnik do starego pamięci:

   ```cpp
   pHeapTracker->ReallocateEvent(memPtrNew, size, memPtrOld);
   ```

   lub:

   ```C
   VSHeapTrackerReallocateEvent(hHeapTracker, memPtrNew, size, memPtrOld);
   ```

1. Na koniec, aby zamknąć i wyczyścić śledzenie stosu niestandardowych w języku C++, należy użyć `CHeapTracker` destruktora, ręcznie lub za pośrednictwem standardowe zasady zakresu, lub `CloseHeapTracker` funkcji w C:

   ```cpp
   delete pHeapTracker;
   ```

   lub:

   ```C
   CloseHeapTracker(hHeapTracker);
   ```

## <a name="track-memory-usage"></a>Śledzenie użycia pamięci
Za pomocą tych wywołań w miejscu użycia niestandardowego sterty teraz można śledzić przy użyciu standardu **użycie pamięci** narzędzia w programie Visual Studio.  Aby uzyskać więcej informacji na temat używania tego narzędzia, zobacz [użycie pamięci](../profiling/memory-usage.md) dokumentacji. Upewnij się, że włączono profilowanie sterty z migawkami, w przeciwnym razie nie będzie mógł przeglądać użycie niestandardowych sterty wyświetlane.

![Włącz profilowanie sterty](media/heap-enable-heap.png)

Aby wyświetlić swoje niestandardowe sterty, śledzenie, użyj **sterty** listy rozwijanej znajduje się w prawym górnym rogu **migawki** okna, aby zmienić widok z *sterta NT* do własnego stosu jako o nazwie wcześniej.

![Wybór sterty](media/heap-example-custom-heap.png)

Za pomocą powyższego przykładu kodu za pomocą `MemoryPool` tworzenia `VSHeapTracker::CHeapTracker` obiektu, a własną `allocate` teraz podczas wywoływania metody `AllocateEvent` metody będą teraz widoczne wynik tego niestandardowego alokacji przedstawiający trzy wystąpienia sumowanie 24 bajty z Typ `Foo`.

Wartość domyślna *sterta NT* sterty wygląda tak samo jak wcześniej dodając naszych `CHeapTracker` obiektu.

![Sterta NT za pomocą śledzenia](media/heap-example-windows-heap.png)

Przy użyciu standardowego stosu Windows, można używać to narzędzie do porównywania migawek i poszukaj przecieków i uszkodzenie w niestandardowych stosu, który jest opisany w głównym [użycie pamięci](../profiling/memory-usage.md) dokumentacji.

> [!TIP]
> Program Visual Studio zawiera także **użycie pamięci** narzędzia w **profilowanie wydajności** zestawu narzędzi, które zostały włączone w **debugowania**  >   **Profiler wydajności** opcji menu lub **Alt**+**F2** za pomocą klawiatury w połączeniu.  Ta funkcja nie obejmuje śledzenia stosu i nie będą wyświetlane na swojej niestandardowej sterty, zgodnie z opisem w tym miejscu.  Tylko **narzędzia diagnostyczne** okno, które można włączyć za pomocą **debugowania** > **Windows** > **Pokaż narzędzia diagnostyczne**  menu lub **Ctrl**+**Alt**+**F2** połączenie za pomocą klawiatury, zawiera tę funkcję.

## <a name="see-also"></a>Zobacz także
[Pierwsze spojrzenie na profilowanie narzędzia](../profiling/profiling-feature-tour.md)
[użycie pamięci](../profiling/memory-usage.md)
