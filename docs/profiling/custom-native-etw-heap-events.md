---
title: Niestandardowe zdarzenia sterty ETW natywnej | Dokumenty firmy Microsoft
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
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "62552964"
---
# <a name="custom-native-etw-heap-events"></a>Niestandardowe zdarzenia ETW sterty natywnej

Visual Studio zawiera wiele [narzędzi profilowania i diagnostyki,](../profiling/profiling-feature-tour.md)w tym natywnego profilera pamięci.  Ten profiler haki [etw zdarzeń](/windows-hardware/drivers/devtest/event-tracing-for-windows--etw-) od dostawcy sterty i zapewnia analizę, jak pamięć jest przydzielany i używany.  Domyślnie to narzędzie może analizować tylko alokacje wykonane ze standardowej sterty systemu Windows, a wszelkie alokacje poza tym macierzystym stosem nie będą wyświetlane.

Istnieje wiele przypadków, w których można użyć własnego sterty niestandardowej i uniknąć narzutów alokacji ze standardowego stosu.  Na przykład można użyć [VirtualAlloc](/windows/desktop/api/memoryapi/nf-memoryapi-virtualalloc) przeznaczyć dużą ilość pamięci na początku aplikacji lub gry, a następnie zarządzać własne bloki w tej liście.  W tym scenariuszu narzędzie profiler pamięci będzie tylko zobaczyć, że alokacja początkowa, a nie niestandardowe zarządzanie wykonane wewnątrz fragmentu pamięci.  Jednak za pomocą dostawcy ETW natywnej sterty niestandardowej można poinformować narzędzie o wszelkich alokacjach, które są wykonane poza standardową stertą.

Na przykład w projekcie, takim `MemoryPool` jak następujące, gdzie jest stos niestandardowy, będzie wyświetlany tylko pojedyncza alokacja na stercie systemu Windows:

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

Migawka z narzędzia [Użycie pamięci](../profiling/memory-usage.md) bez niestandardowego śledzenia sterty pokaże tylko pojedynczą alokację bajtów 8192 i żadna z alokacji niestandardowych dokonywanych przez pulę:

![Alokacja sterty systemu Windows](media/heap-example-windows-heap.png)

Wykonując następujące kroki, możemy użyć tego samego narzędzia do śledzenia usgae pamięci w naszym stercie niestandardowej.

## <a name="how-to-use"></a>Jak stosować

Ta biblioteka może być łatwo używana w językach C i C++.

1. Dołącz nagłówek dostawcy niestandardowego dostawcy ETW sterty niestandardowej:

   ```cpp
   #include <VSCustomNativeHeapEtwProvider.h>
   ```

1. Dodaj `__declspec(allocator)` dekoratora do dowolnej funkcji w menedżerze sterty niestandardowej, która zwraca wskaźnik do nowo przydzielonej pamięci sterty.  Ten dekorator pozwala narzędziu poprawnie zidentyfikować typ zwracanej pamięci.  Przykład:

   ```cpp
   __declspec(allocator) void *MyMalloc(size_t size);
   ```

   > [!NOTE]
   > Ten dekorator powie kompilator, że ta funkcja jest wywołaniem alokatora.  Każde wywołanie funkcji spowoduje wysunie adres callite, rozmiar instrukcji wywołania i typeId `S_HEAPALLOCSITE` nowego obiektu do nowego symbolu.  Po przydzieleniu przydzieleniu przydzielynia połączenia system Windows emituje zdarzenie ETW z tymi informacjami.  Narzędzie profilera pamięci przechodzi callstack szuka adresu `S_HEAPALLOCSITE` zwrotnego pasujące do symbolu i typeId informacji w symbolu jest używany do wyświetlania typu środowiska wykonawczego alokacji.
   >
   > Krótko mówiąc, oznacza to, `(B*)(A*)MyMalloc(sizeof(B))` że połączenie, które wygląda, `B`pojawi `void` się `A`w narzędziu jako typ , nie lub .

1. W przypadku języka C++ utwórz `VSHeapTracker::CHeapTracker` obiekt, podając nazwę sterty, która pojawi się w narzędziu profilowania:

   ```cpp
   auto pHeapTracker = std::make_unique<VSHeapTracker::CHeapTracker>("MyCustomHeap");
   ```

   Jeśli używasz języka C, użyj `OpenHeapTracker` tej funkcji.  Ta funkcja zwróci dojście, którego będziesz używać podczas wywoływania innych funkcji śledzenia:

   ```C
   VSHeapTrackerHandle hHeapTracker = OpenHeapTracker("MyHeap");
   ```

1. Podczas przydzielania pamięci przy użyciu funkcji `AllocateEvent` niestandardowej, wywołać (C++) lub `VSHeapTrackerAllocateEvent` (C) metoda, przekazywanie w wskaźniku do pamięci i jej rozmiar, aby śledzić alokacji:

   ```cpp
   pHeapTracker->AllocateEvent(memPtr, size);
   ```

   lub

   ```C
   VSHeapTrackerAllocateEvent(hHeapTracker, memPtr, size);
   ```

   > [!IMPORTANT]
   > Nie zapomnij oznaczyć niestandardowej funkcji alokatora za pomocą opisanego `__declspec(allocator)` wcześniej dekoratora.

1. Podczas przydzielania pamięci przy użyciu funkcji `DeallocateEvent` niestandardowej, wywołać (C++) lub `VSHeapTracerDeallocateEvent` (C) funkcji, przechodząc w wskaźniku do pamięci, aby śledzić alokacji:

   ```cpp
   pHeapTracker->DeallocateEvent(memPtr);
   ```

   lub:

   ```C
   VSHeapTrackerDeallocateEvent(hHeapTracker, memPtr);
   ```

1. Podczas ponownego przydzielania pamięci przy użyciu `ReallocateEvent` funkcji niestandardowej, `VSHeapReallocateEvent` wywołać (C++) lub (C) metoda, przekazywanie wskaźnika do nowej pamięci, rozmiar alokacji i wskaźnik do starej pamięci:

   ```cpp
   pHeapTracker->ReallocateEvent(memPtrNew, size, memPtrOld);
   ```

   lub:

   ```C
   VSHeapTrackerReallocateEvent(hHeapTracker, memPtrNew, size, memPtrOld);
   ```

1. Na koniec, aby zamknąć i oczyścić niestandardowy moduł śledzenia `CHeapTracker` sterty w języku C++, użyj destruktora ręcznie lub za pomocą standardowych reguł określania zakresu lub `CloseHeapTracker` funkcji w języku C:

   ```cpp
   delete pHeapTracker;
   ```

   lub:

   ```C
   CloseHeapTracker(hHeapTracker);
   ```

## <a name="track-memory-usage"></a>Śledzenie użycia pamięci
Z tych wywołań w miejscu, niestandardowe użycie sterty można teraz śledzić przy użyciu standardowego narzędzia **użycia pamięci** w programie Visual Studio.  Aby uzyskać więcej informacji na temat korzystania z tego narzędzia, zobacz dokumentację [użycia pamięci.](../profiling/memory-usage.md) Upewnij się, że włączono profilowanie sterty za pomocą migawek, w przeciwnym razie nie zostanie wyświetlone niestandardowe użycie sterty.

![Włącz profilowanie sterty](media/heap-enable-heap.png)

Aby wyświetlić niestandardowe śledzenie sterty, użyj listy rozwijanej **Sterta** znajdującej się w prawym górnym rogu okna **Migawka,** aby zmienić widok z *sterty NT* na własną stertę, jak nazwano wcześniej.

![Wybór sterty](media/heap-example-custom-heap.png)

Korzystając z powyższego `MemoryPool` przykładu `VSHeapTracker::CHeapTracker` kodu, z `allocate` utworzeniem obiektu `AllocateEvent` i naszą własną metodą teraz wywołującą metodę, można teraz zobaczyć wynik tej `Foo`alokacji niestandardowej, pokazując trzy wystąpienia o łącznej liczbie 24 bajtów, wszystkie typu .

Domyślna *sterty sterty NT* wygląda tak samo jak `CHeapTracker` wcześniej, z dodatkiem naszego obiektu.

![Sterta NT z trackerem](media/heap-example-windows-heap.png)

Podobnie jak w przypadku standardowej sterty systemu Windows, można również użyć tego narzędzia do porównywania migawek i wyszukiwania przecieków i uszkodzenia w stercie niestandardowej, która jest opisana w głównej dokumentacji [użycia pamięci.](../profiling/memory-usage.md)

> [!TIP]
> Visual Studio zawiera również narzędzie **Użycie pamięci** w zestawie narzędzi **profilowania wydajności,** który jest włączony **Alt**z opcji menu+ **debugowania** > **profilera wydajności** lub kombinacji klawiatury Alt**F2.**  Ta funkcja nie obejmuje śledzenia sterty i nie będzie wyświetlać niestandardowego stosu, jak opisano w tym miejscu.  Tylko okno **Narzędzia diagnostyczne,** które można włączyć za pomocą menu **Debugowanie** > **narzędzi diagnostycznych pokazu** systemu**Windows** > lub kombinacji klawiatury **Ctrl**+**Alt**+**F2,** zawiera tę funkcję.

## <a name="see-also"></a>Zobacz też
[Pierwsze spojrzenie na narzędzia](../profiling/profiling-feature-tour.md)
do profilowania[Użycie pamięci](../profiling/memory-usage.md)
