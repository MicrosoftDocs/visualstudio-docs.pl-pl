---
title: Niestandardowe zdarzenia natywnej sterty ETW | Microsoft Docs
description: Dowiedz się, w jaki sposób używać sterty niestandardowej, aby zmniejszyć obciążenie związane z alokacją, ale nadal dostarczaj informacje o alokacji do profilera pamięci na potrzeby analizy alokacji.
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: 61005bf108d0dab16ec419e942e3da97e02cdc7f
ms.sourcegitcommit: d13f7050c873b6284911d1f4acf07cfd29360183
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/22/2021
ms.locfileid: "98686327"
---
# <a name="custom-native-etw-heap-events"></a>Niestandardowe zdarzenia ETW sterty natywnej

Program Visual Studio zawiera różnorodne [Narzędzia do profilowania i diagnostyki](../profiling/profiling-feature-tour.md), w tym Profiler pamięci natywnej.  Ten Profiler przechwytuje [zdarzenia ETW](/windows-hardware/drivers/devtest/event-tracing-for-windows--etw-) z dostawcy sterty i zapewnia analizę sposobu przydzielania i używania pamięci.  Domyślnie to narzędzie może analizować tylko alokacje wykonane ze standardowej sterty systemu Windows, a wszelkie alokacje poza tą stertą natywną nie będą wyświetlane.

Istnieje wiele przypadków, w których warto użyć własnego sterty niestandardowej i uniknąć narzutu przydziału ze sterty standardowej.  Na przykład można użyć [Funkcja VirtualAlloc](/windows/desktop/api/memoryapi/nf-memoryapi-virtualalloc) do przydzielania dużej ilości pamięci na początku aplikacji lub gry, a następnie zarządzania własnymi blokami na tej liście.  W tym scenariuszu Narzędzie Memory Profiler widzi tylko tę początkową alokację, a nie niestandardowe zarządzanie w ramach fragmentu pamięci.  Jednak przy użyciu niestandardowego dostawcy funkcji ETW sterty natywnej można pozwolić narzędziu na informacje o wszelkich przydziałach tworzonych poza stertą standardową.

Na przykład w projekcie podobnym do poniższego `MemoryPool` , gdzie jest stertą niestandardową, zostanie wyświetlona tylko jedna alokacja na stercie systemu Windows:

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

Migawka z narzędzia [użycie pamięci](../profiling/memory-usage.md) bez niestandardowego śledzenia sterty będzie zawierać tylko jedną 8192 bajtów alokacji, a żaden z przydziałów niestandardowych nie zostanie wykonany przez pulę:

![Alokacja sterty systemu Windows](media/heap-example-windows-heap.png)

Wykonując poniższe kroki, można użyć tego samego narzędzia do śledzenia użycia pamięci w naszym stosie niestandardowym.

## <a name="how-to-use"></a>Sposób użycia

Ta biblioteka może być łatwo używana w językach C i C++.

1. Dołącz nagłówek niestandardowego dostawcy ETW sterty:

   ```cpp
   #include <VSCustomNativeHeapEtwProvider.h>
   ```

1. Dodaj `__declspec(allocator)` dekoratora do dowolnej funkcji w Menedżerze sterty niestandardowych, która zwraca wskaźnik do nowo przydzieloną pamięć sterty.  Ta dekoratora umożliwia poprawne zidentyfikowanie typu zwracanej pamięci przez narzędzie.  Przykład:

   ```cpp
   __declspec(allocator) void *MyMalloc(size_t size);
   ```

   > [!NOTE]
   > Ten dekoratora informuje kompilator, że ta funkcja jest wywołaniem do alokatora.  Każde wywołanie funkcji będzie wyprowadzać adres szczegóły, rozmiar instrukcji wywołania i identyfikator elementu nowego obiektu do nowego `S_HEAPALLOCSITE` symbolu.  Po przydzieleniu stosu wywołań system Windows emituje zdarzenie ETW z tymi informacjami.  Narzędzie Memory Profiler sprawdza stosu wywołań w poszukiwaniu adresu zwrotnego odpowiadającego `S_HEAPALLOCSITE` symbolowi, a informacje o identyfikatorze w symbolu są używane do wyświetlania typu czasu wykonywania alokacji.
   >
   > W skrócie oznacza to, że wywołanie, które wygląda tak, `(B*)(A*)MyMalloc(sizeof(B))` będzie widoczne w narzędziu jako typ `B` , `void` a nie lub `A` .

1. Dla języka C++ Utwórz `VSHeapTracker::CHeapTracker` obiekt, podając nazwę sterty, która będzie wyświetlana w narzędziu profilowania:

   ```cpp
   auto pHeapTracker = std::make_unique<VSHeapTracker::CHeapTracker>("MyCustomHeap");
   ```

   Jeśli używasz języka C, `OpenHeapTracker` zamiast tego użyj funkcji.  Ta funkcja zwróci uchwyt, który będzie używany podczas wywoływania innych funkcji śledzenia:

   ```C
   VSHeapTrackerHandle hHeapTracker = OpenHeapTracker("MyHeap");
   ```

1. W przypadku przydzielania pamięci przy użyciu funkcji niestandardowej Wywołaj `AllocateEvent` metodę (C++) lub `VSHeapTrackerAllocateEvent` (C), przekazując wskaźnik do pamięci i jej rozmiaru, aby śledzić alokację:

   ```cpp
   pHeapTracker->AllocateEvent(memPtr, size);
   ```

   lub

   ```C
   VSHeapTrackerAllocateEvent(hHeapTracker, memPtr, size);
   ```

   > [!IMPORTANT]
   > Nie zapomnij, aby oznaczyć funkcję alokatora niestandardowego przy użyciu `__declspec(allocator)` opisanego wcześniej dekoratora.

1. Podczas cofania przydziału pamięci przy użyciu funkcji niestandardowej, wywołaj `DeallocateEvent` funkcję (C++) lub `VSHeapTracerDeallocateEvent` (C), przekazując wskaźnik do pamięci, aby śledzić Cofnięcie alokacji:

   ```cpp
   pHeapTracker->DeallocateEvent(memPtr);
   ```

   lub:

   ```C
   VSHeapTrackerDeallocateEvent(hHeapTracker, memPtr);
   ```

1. Podczas ponownego przydzielania pamięci przy użyciu funkcji niestandardowej, wywołaj `ReallocateEvent` metodę (C++) lub `VSHeapReallocateEvent` (C), przekazując wskaźnik do nowej pamięci, rozmiar alokacji i wskaźnik do starej pamięci:

   ```cpp
   pHeapTracker->ReallocateEvent(memPtrNew, size, memPtrOld);
   ```

   lub:

   ```C
   VSHeapTrackerReallocateEvent(hHeapTracker, memPtrNew, size, memPtrOld);
   ```

1. Na koniec aby zamknąć i oczyścić niestandardowe śledzenie sterty w języku C++, użyj `CHeapTracker` destruktora ręcznie lub za pomocą standardowych zasad określania zakresu lub `CloseHeapTracker` funkcji w C:

   ```cpp
   delete pHeapTracker;
   ```

   lub:

   ```C
   CloseHeapTracker(hHeapTracker);
   ```

## <a name="track-memory-usage"></a>Śledzenie użycia pamięci
W przypadku tych wywołań niestandardowe użycie sterty będzie teraz śledzone przy użyciu standardowego narzędzia **użycie pamięci** w programie Visual Studio.  Aby uzyskać więcej informacji na temat korzystania z tego narzędzia, zobacz dokumentację dotyczącą [użycia pamięci](../profiling/memory-usage.md) . Upewnij się, że włączono profilowanie sterty z migawkami, w przeciwnym razie nie zobaczysz niestandardowego użycia sterty.

![Włącz profilowanie sterty](media/heap-enable-heap.png)

Aby wyświetlić niestandardowe śledzenie sterty, Użyj listy rozwijanej **sterty** znajdującej się w prawym górnym rogu okna **migawki** , aby zmienić widok *sterty systemu NT* na własne stertę jako nazwę wcześniej.

![Wybór sterty](media/heap-example-custom-heap.png)

Korzystając z powyższego przykładu kodu, przy `MemoryPool` tworzeniu `VSHeapTracker::CHeapTracker` obiektu i naszej `allocate` metodzie wywołującej `AllocateEvent` metodę, można teraz zobaczyć wynik tej niestandardowej alokacji, pokazując trzy wystąpienia łącznie 24 bajty, wszystkie typu `Foo` .

Domyślna sterta *sterty systemu NT* wygląda tak samo jak wcześniej, z dodaniem naszego `CHeapTracker` obiektu.

![Sterta NT z narzędziem do śledzenia](media/heap-example-windows-heap.png)

Podobnie jak w przypadku standardowej sterty systemu Windows, można również użyć tego narzędzia do porównania migawek i wyszukania przecieków i uszkodzenia w stosie niestandardowym, który jest opisany w dokumentacji [dotyczącej użycia pamięci](../profiling/memory-usage.md) głównej.

> [!TIP]
> Program Visual Studio zawiera również narzędzie **użycie pamięci** w narzędziu **profilowania wydajności** , które jest włączone z poziomu   >  opcji menu **profilera wydajności** debugowania lub  + kombinacji klawiaturowej ALT **F2** .  Ta funkcja nie obejmuje śledzenia sterty i nie będzie wyświetlać sterty niestandardowej zgodnie z opisem w tym miejscu.  Ta funkcja jest dostępna tylko w oknie **Narzędzia diagnostyczne** , które można włączyć za pomocą menu **Debuguj**  >    >  **Narzędzia diagnostyczne Windows show** lub kombinacji **klawiszy CTRL** + **Alt** + **F2** .

## <a name="see-also"></a>Zobacz też
[Pierwsze spojrzenie na narzędzia profilowania](../profiling/profiling-feature-tour.md) 
 [Użycie pamięci](../profiling/memory-usage.md)
