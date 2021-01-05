---
title: Mierzenie użycia pamięci w aplikacjach
description: Znajdowanie przecieków pamięci i niewydajnej pamięci podczas debugowania za pomocą narzędzia diagnostycznego zintegrowanego z debugerem.
ms.custom: seodec18
ms.date: 04/25/2018
ms.topic: tutorial
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 3d259c6fa69821d1fecd26944227bff86cc82104
ms.sourcegitcommit: 105e7b5a486262bc92939980383ceee068098a11
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/30/2020
ms.locfileid: "97815857"
---
# <a name="measure-memory-usage-in-visual-studio"></a>Mierzenie użycia pamięci w programie Visual Studio

Znajdowanie przecieków pamięci i niewydajnej pamięci podczas debugowania za pomocą narzędzia diagnostycznego **dotyczącego użycia pamięci** zintegrowanej z debugerem. Narzędzie użycie pamięci pozwala wykonać jedną lub więcej *migawek* sterty pamięci zarządzanej i natywnej, aby ułatwić zrozumienie wpływu użycia pamięci przez typy obiektów. Możesz również analizować użycie pamięci bez debugera lub przeznaczoną dla działającej aplikacji. Aby uzyskać więcej informacji, zobacz [Uruchamianie narzędzi profilowania z debugerem lub bez niego](../profiling/running-profiling-tools-with-or-without-the-debugger.md).

Chociaż w dowolnym momencie można zbierać migawki pamięci w narzędziu **użycie pamięci** , można użyć debugera programu Visual Studio, aby kontrolować sposób wykonywania aplikacji podczas badania problemów z wydajnością. Ustawianie punktów przerwania, krokowe, przerwanie i inne akcje debugera mogą pomóc skupić się na dochodzeniu do wydajności na najbardziej istotnych ścieżkach kodu. Wykonywanie tych akcji, gdy aplikacja jest uruchomiona, może wyeliminować szum z kodu, który nie jest interesujący, i może znacznie skrócić czas, w którym można zdiagnozować problem.

> [!Important]
> Narzędzia diagnostyczne zintegrowane z debugerem są obsługiwane przez Programowanie dla platformy .NET w programie Visual Studio, w tym ASP.NET, ASP.NET Core, programowanie natywne/C++ oraz aplikacje trybu mieszanego (.NET i Native). System Windows 8 lub nowszy jest wymagany do uruchamiania narzędzi profilowania przy użyciu debugera (okno **Narzędzia diagnostyczne** ).

W tym samouczku wykonasz następujące czynności:

> [!div class="checklist"]
> * Wykonaj migawki pamięci
> * Analizowanie danych użycia pamięci

Jeśli **użycie pamięci** nie daje potrzebnych danych, inne narzędzia profilowania w [profilerze wydajności](../profiling/profiling-feature-tour.md#post_mortem) zapewniają różne rodzaje informacji, które mogą być przydatne dla użytkownika. W wielu przypadkach wąskie gardła wydajności aplikacji może być spowodowane przez coś innego niż pamięć, takich jak procesor CPU, interfejs użytkownika renderowania lub czas żądania sieci.

> [!NOTE]
> **Obsługa alokatora niestandardowego** Profiler pamięci natywnej działa przez zbieranie danych zdarzeń [ETW](/windows-hardware/drivers/devtest/event-tracing-for-windows--etw-) alokacji emitowanych w czasie wykonywania.  Przydziały w CRT i Windows SDK zostały opatrzone adnotacją na poziomie źródła, aby można było przechwytywać ich dane alokacji. W przypadku pisania własnych przydziałów, wszystkie funkcje, które zwracają wskaźnik do nowo przydzieloną pamięci sterty, mogą mieć [__declspec](/cpp/cpp/declspec)(Alokator), jak pokazano w tym przykładzie dla elementu malloc:
>
> `__declspec(allocator) void* myMalloc(size_t size)`

## <a name="collect-memory-usage-data"></a>Zbieranie danych użycia pamięci

1. Otwórz projekt, który chcesz debugować w programie Visual Studio, i ustaw punkt przerwania w aplikacji w punkcie, w którym chcesz rozpocząć badanie użycia pamięci.

    Jeśli masz obszar, w którym podejrzewasz problem z pamięcią, ustaw pierwszy punkt przerwania przed wystąpieniem problemu z pamięcią.

    > [!TIP]
    > Ponieważ może być trudne do przechwycenia profilu pamięci operacji, która interesuje Cię, gdy aplikacja często przydziela i cofa alokację pamięci, ustaw punkty przerwania na początku i na końcu operacji (lub przechodząc przez operację), aby znaleźć dokładny punkt zmiany pamięci.

2. Ustaw drugi punkt przerwania na końcu funkcji lub regionu kodu, który chcesz analizować (lub po wystąpieniu problemu z pamięcią).

3. Okno **Narzędzia diagnostyczne** jest automatycznie wyświetlane, chyba że zostało wyłączone. Aby ponownie wyświetlić okno, kliknij pozycję **Debuguj**  >  **okna**  >  **Pokaż narzędzia diagnostyczne**.

4. Wybierz opcję **użycie pamięci** z ustawieniem **Wybierz Narzędzia** na pasku narzędzi.

     ![Pokaż narzędzia diagnostyczne](../profiling/media/diag-tools-select-tool-2.png "DiagToolsSelectTool")

5. Kliknij pozycję **Debuguj/Rozpocznij debugowanie** (lub **Rozpocznij** na pasku narzędzi lub **F5**).

     Po zakończeniu ładowania aplikacji zostanie wyświetlony widok Podsumowanie narzędzi diagnostycznych.

     ![Karta Podsumowanie narzędzi diagnostycznych](../profiling/media/diag-tools-summary-tab-2.png "DiagToolsSummaryTab")

     > [!NOTE]
     > Ponieważ zbieranie danych pamięci może mieć wpływ na wydajność debugowania aplikacji w trybie macierzystym lub mieszanym, migawki pamięci są domyślnie wyłączone. Aby włączyć migawki w aplikacjach w trybie macierzystym lub mieszanym, uruchom sesję debugowania (klawisz skrótu: **F5**). Po wyświetleniu okna **Narzędzia diagnostyczne** wybierz kartę **użycie pamięci** , a następnie wybierz pozycję **profilowanie sterty**.
     >
     >  ![Włącz migawki](../profiling/media/dbgdiag_mem_mixedtoolbar_enablesnapshot.png "DBGDIAG_MEM_MixedToolbar_EnableSnapshot")
     >
     >  Zatrzymaj (klawisz skrótu: **SHIFT** + **F5**) i uruchom ponownie debugowanie.

6. Aby utworzyć migawkę na początku sesji debugowania, wybierz pozycję **Wykonaj migawkę** na pasku narzędzi podsumowania **użycia pamięci** . (Może to ułatwić również ustawienie punktu przerwania).

    ![Utwórz migawkę](../profiling/media/dbgdiag_mem_mixedtoolbar_takesnapshot.png "DBGDIAG_MEM_MixedToolbar_TakeSnapshot")

     > [!TIP]
     > Aby utworzyć linię bazową dla porównywania pamięci, rozważ wykonanie migawki na początku sesji debugowania.

6. Uruchom scenariusz, który spowoduje, że pierwszy punkt przerwania zostanie osiągnięty.

7. Gdy debuger jest wstrzymany przy pierwszym punkcie przerwania, wybierz pozycję **zrób migawkę** na pasku narzędzi podsumowanie **użycia pamięci** .

8. Naciśnij klawisz **F5** , aby uruchomić aplikację w drugim punkcie przerwania.

9. Teraz Utwórz kolejną migawkę.

     W tym momencie można rozpocząć analizowanie danych.

## <a name="analyze-memory-usage-data"></a>Analizowanie danych użycia pamięci
W tabeli podsumowania użycia pamięci wymieniono migawki, które zostały wykonane podczas sesji debugowania i przedstawiono linki do bardziej szczegółowych widoków.

![Tabela podsumowania pamięci](../profiling/media/dbgdiag_mem_summarytable.png "DBGDIAG_MEM_SummaryTable")

 Nazwy kolumn zależą od trybu debugowania wybranego we właściwościach projektu: .NET, native lub Mixed (zarówno .NET, jak i Native).

- Kolumny **obiekty (diff)** i **Alokacje (diff)** wyświetlają liczbę obiektów w programie .NET i pamięci natywnej podczas tworzenia migawki.

- Kolumna **rozmiar sterty (różnica)** zawiera liczbę bajtów w stercie .NET i natywnych stert

Po wykonaniu wielu migawek komórki tabeli podsumowującej obejmują zmianę wartości między migawką wiersza a poprzednią migawką.

Aby analizować użycie pamięci, kliknij jedno z linków otwierających szczegółowy raport o wykorzystaniu pamięci:

- Aby wyświetlić szczegóły różnicy między bieżącą migawką i poprzednią migawką, wybierz link Zmień z lewej strony strzałki (![Zwiększ użycie pamięci](../profiling/media/prof-tour-mem-usage-up-arrow.png "Zwiększenie użycia pamięci")). Czerwona strzałka wskazuje zwiększenie użycia pamięci i zieloną strzałkę wskazującą spadek.

> [!TIP]
> Aby szybciej identyfikować problemy z pamięcią, raporty różnicowe są sortowane według typów obiektów, które zwiększyły największą liczbę całkowitą (kliknij kolumnę Zmień łącze w **obiektach (diff)** ) lub który zwiększył największą rozmiar sterty (kliknij łącze Zmień w **rozmiarze sterty** ).

- Aby wyświetlić szczegóły tylko wybranej migawki, kliknij link bez zmian.

   Raport zostanie wyświetlony w osobnym oknie.

### <a name="managed-types-reports"></a>Raporty typów zarządzanych
 Wybierz bieżące łącze do komórki **Objects (diff)** lub **alokacji (diff)** w tabeli Podsumowanie użycia pamięci.

 ![Debuger typu zarządzanego dla debugera &#45; ścieżki do katalogu głównego](../profiling/media/dbgdiag_mem_managedtypesreport_pathstoroot.png "DBGDIAG_MEM_ManagedTypesReport_PathsToRoot")

 Górne okienko pokazuje liczbę i rozmiar typów w migawce, w tym rozmiar wszystkich obiektów, do których odwołuje się typ (**rozmiar włącznie**).

 **Ścieżki do drzewa głównego** w dolnym okienku wyświetla obiekty odwołujące się do typu wybranego w górnym okienku. Moduł wyrzucania elementów bezużytecznych platformy .NET czyści pamięć dla obiektu tylko wtedy, gdy został opublikowany ostatni typ, który odwołuje się do niego.

 Drzewo **przywoływanych obiektów** wyświetla odwołania, które są przechowywane przez typ wybrany w górnym okienku.

 ![Widok raportu zarządzanych obiektów, do których istnieją odwołania](../profiling/media/dbgdiag_mem_managedtypesreport_referencedtypes.png "DBGDIAG_MEM_ManagedTypesReport_ReferencedTypes")

 Aby wyświetlić wystąpienia wybranego typu w górnym okienku, wybierz ikonę ![wystąpienia](../profiling/media/dbgdiag_mem_instanceicon.png "DBGDIAG_MEM_InstanceIcon") ikona.

 ![Zrzut ekranu przedstawiający Widok wystąpień w narzędziu Użycie pamięci programu Visual Studio, w okienku wystąpienia i ścieżki do okienka obiekty główne i odwołania.](../profiling/media/dbgdiag_mem_managedtypesreport_instances.png "DBGDIAG_MEM_ManagedTypesReport_Instances")

 Widok **wystąpienia** wyświetla wystąpienia wybranego obiektu w migawce w górnym okienku. Okienko **ścieżki do katalogu głównego** i **przywoływanych obiektów** wyświetla obiekty odwołujące się do wybranego wystąpienia i typy, do których odwołuje się wybrane wystąpienie. Gdy debuger zostanie zatrzymany w punkcie, w którym zrobiono migawkę, możesz umieścić wskaźnik myszy nad komórką **wartości** , aby wyświetlić wartości obiektu w etykietce narzędzia.

### <a name="native-type-reports"></a>Raporty typu natywnego
 Wybierz bieżące łącze do komórki **alokacji (diff)** lub **rozmiaru sterty (diff)** w tabeli podsumowania użycia pamięci okna **Narzędzia diagnostyczne** .

 ![Widok typu natywnego](../profiling/media/dbgdiag_mem_native_typesview.png "DBGDIAG_MEM_Native_TypesView")

 **Widok typy** wyświetla liczbę i rozmiar typów w migawce.

- Wybierz ikonę wystąpienia (![ikona wystąpienia w kolumnie Typ obiektu](../profiling/media/dbg_mma_instancesicon.png "DBG_MMA_InstancesIcon")) wybranego typu, aby wyświetlić informacje o obiektach wybranego typu w migawce.

     Widok **wystąpienia** wyświetla każde wystąpienie wybranego typu. Wybranie wystąpienia powoduje wyświetlenie stosu wywołań, który spowodowało utworzenie wystąpienia w okienku **stosu wywołań alokacji** .

     ![Zrzut ekranu przedstawiający Widok wystąpień w narzędziu Użycie pamięci programu Visual Studio, w okienku wystąpienia i w okienku stos wywołań alokacji.](../profiling/media/dbgdiag_mem_native_instances.png "DBGDIAG_MEM_Native_Instances")

- Wybierz **Widok stosów** na liście **tryb wyświetlania** , aby wyświetlić stos alokacji dla wybranego typu.

     ![Widok stosów](../profiling/media/dbgdiag_mem_native_stacksview.png "DBGDIAG_MEM_Native_StacksView")

### <a name="change-diff-reports"></a>Raporty zmian (diff)

- Wybierz łącze Zmień w komórce tabeli podsumowującej karty **użycie pamięci** w oknie **Narzędzia diagnostyczne** .

   ![Wybierz raport &#40;różnic&#41;](../profiling/media/dbgdiag_mem_choosediffreport.png "DBGDIAG_MEM_ChooseDiffReport")

- Wybierz migawkę na liście **Porównaj z** w raporcie zarządzanym lub natywnym.

   ![Wybierz migawkę z listy Porównaj z](../profiling/media/dbgdiag_mem_choosecompareto.png "DBGDIAG_MEM_ChooseCompareTo")

Raport zmiana dodaje kolumny (oznaczone atrybutem **(diff)**) do raportu podstawowego, który pokazuje różnicę między podstawową wartością migawki a migawką porównania. Oto jak wygląda raport różnicowy widoku typu natywnego:

![Widok różnic typów natywnych](../profiling/media/dbgdiag_mem_native_typesviewdiff.png "DBGDIAG_MEM_Native_TypesViewDiff")

## <a name="blogs-and-videos"></a>Blogi i filmy wideo

[Analizuj procesor i pamięć podczas debugowania](https://devblogs.microsoft.com/visualstudio/analyze-cpu-memory-while-debugging/)

[Blog Visual C++: Profilowanie pamięci w Visual C++ 2015](https://devblogs.microsoft.com/cppblog/memory-profiling-in-visual-c-2015/)

## <a name="next-steps"></a>Następne kroki

W tym samouczku przedstawiono sposób zbierania i analizowania danych użycia pamięci. Jeśli [samouczek](../profiling/profiling-feature-tour.md)został już ukończony, warto zapoznać się z tematem jak analizować użycie procesora w aplikacjach.

> [!div class="nextstepaction"]
> [Analizowanie użycia procesora CPU](../profiling/beginners-guide-to-performance-profiling.md)
