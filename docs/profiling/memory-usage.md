---
title: Mierzenie użycia pamięci w aplikacjach
description: Znajdź przecieki pamięci i nieefektywną pamięć podczas debugowania za pomocą narzędzia diagnostycznego zintegrowanego z debugerem.
ms.custom: seodec18
ms.date: 04/25/2018
ms.topic: tutorial
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: dc0d97b1e2b2e27ebc8ddb898795c1767155c1cb
ms.sourcegitcommit: ee12b14f306ad8f49b77b08d3a16d9f54426e7ca
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/25/2020
ms.locfileid: "80256195"
---
# <a name="measure-memory-usage-in-visual-studio"></a>Mierzenie użycia pamięci w programie Visual Studio

Znajdź przecieki pamięci i nieefektywną pamięć podczas debugowania za pomocą narzędzia diagnostycznego **użycia pamięci** zintegrowanego z debugerem. Narzędzie Użycie pamięci umożliwia podjęcie co najmniej jednej *migawki* zarządzanego i natywnego stosu pamięci, aby ułatwić zrozumienie wpływu użycia pamięci typów obiektów. Można zbierać migawki aplikacji .NET, natywnych lub mieszanych (.NET i natywnych).

Na poniższej ilustracji przedstawiono okno **Narzędzia diagnostyczne** (dostępne w programie Visual Studio 2015 Update 1 i nowszych wersjach):

![DiagnosticTools&#45;Update1](../profiling/media/diagnostictools-update1.png "DiagnosticTools-Update1")

Chociaż można zbierać migawki pamięci w dowolnym momencie w narzędziu **Użycie pamięci,** można użyć debugera programu Visual Studio do kontrolowania sposobu wykonywania aplikacji podczas badania problemów z wydajnością. Ustawianie punktów przerwania, stepping, Break All i inne akcje debugera może pomóc skupić badania wydajności na ścieżki kodu, które są najbardziej odpowiednie. Wykonywanie tych akcji, gdy aplikacja jest uruchomiona, może wyeliminować hałas z kodu, który Cię nie interesuje i może znacznie skrócić czas potrzebny do zdiagnozowania problemu.

Można również użyć narzędzia pamięci poza debugerem. Zobacz [Użycie pamięci bez debugowania](../profiling/memory-usage-without-debugging2.md). Można użyć narzędzi profilowania bez debugera dołączonego do systemu Windows 7 i nowszych. System Windows 8 i nowsze są wymagane do uruchamiania narzędzi profilowania za pomocą debugera (okno**Narzędzia diagnostyczne).**

> [!NOTE]
> **Niestandardowa obsługa alokatora** Profiler pamięci natywnej działa przez zbieranie danych zdarzeń [ETW](/windows-hardware/drivers/devtest/event-tracing-for-windows--etw-) alokacji emitowanych w czasie wykonywania.  Alokatory w crt i windows SDK zostały otytułowane na poziomie źródła, dzięki czemu można przechwycić ich dane alokacji. Jeśli piszesz własne alokatory, wszystkie funkcje, które zwracają wskaźnik do nowo przydzielonej pamięci sterty mogą być ozdobione [__declspec](/cpp/cpp/declspec)(alokator), jak widać w tym przykładzie dla myMalloc:
>
> `__declspec(allocator) void* myMalloc(size_t size)`

W tym samouczku zostaną wykonane następujące czynności:

> [!div class="checklist"]
> * Tworzenie migawek pamięci
> * Analizowanie danych użycia pamięci

## <a name="collect-memory-usage-data"></a>Zbieranie danych użycia pamięci

1. Otwórz projekt, który chcesz debugować w programie Visual Studio i ustaw punkt przerwania w aplikacji w punkcie, w którym chcesz rozpocząć badanie użycia pamięci.

    Jeśli masz obszar, w którym podejrzewasz problem z pamięcią, ustaw pierwszy punkt przerwania przed wystąpieniem problemu z pamięcią.

    > [!TIP]
    > Ponieważ przechwytywanie profilu pamięci operacji, która Cię interesuje, gdy aplikacja często przydziela i cofa alokację pamięci, ustawia punkty przerwania na początku i na końcu operacji (lub krok po operacji), aby znaleźć dokładny punkt, który pamięci.

2. Ustaw drugi punkt przerwania na końcu funkcji lub regionu kodu, który chcesz analizować (lub po wystąpieniu podejrzewanego problemu z pamięcią).

3. Okno **Narzędzia diagnostyczne** jest wyświetlane automatycznie, chyba że zostało wyłączone. Aby ponownie wyświetlić okno, kliknij przycisk **Debugowanie** > **narzędzi diagnostycznych programu****Windows** > Show .

4. Wybierz **użycie pamięci** z **ustawieniem Wybierz narzędzia** na pasku narzędzi.

     ![Pokaż narzędzia diagnostyczne](../profiling/media/diag-tools-select-tool-2.png "DiagToolsSelectTool")

5. Kliknij **przycisk Debugowanie / Rozpocznij debugowanie** (lub **Rozpocznij** na pasku narzędzi lub **F5**).

     Po zakończeniu ładowania aplikacji zostanie wyświetlony widok Podsumowanie narzędzi diagnostycznych.

     ![Karta Podsumowanie narzędzi diagnostycznych](../profiling/media/diag-tools-summary-tab-2.png "DiagToolsSummaryTab")

     > [!NOTE]
     > Ponieważ zbieranie danych pamięci może mieć wpływ na wydajność debugowania aplikacji natywnych lub w trybie mieszanym, migawki pamięci są domyślnie wyłączone. Aby włączyć migawki w aplikacjach w trybie macierzystym lub mieszanym, rozpocznij sesję debugowania (klawisz skrótu: **F5**). Po **wyświetleniu** okna Narzędzia diagnostyczne wybierz kartę **Użycie pamięci,** a następnie wybierz pozycję **Profilowanie sterty**.
     >
     >  ![Włączanie migawek](../profiling/media/dbgdiag_mem_mixedtoolbar_enablesnapshot.png "DBGDIAG_MEM_MixedToolbar_EnableSnapshot")
     >
     >  Zatrzymaj (klawisz skrótu: **Shift**+**F5)** i uruchom ponownie debugowanie.

6. Aby zrobić migawkę na początku sesji debugowania, wybierz pozycję **Zrób migawkę** na pasku narzędzi podsumowanie **użycia pamięci.** (Może to pomóc ustawić punkt przerwania tutaj, jak również.)

    ![Tworzenie migawki](../profiling/media/dbgdiag_mem_mixedtoolbar_takesnapshot.png "DBGDIAG_MEM_MixedToolbar_TakeSnapshot")

     > [!TIP]
     > Aby utworzyć linię bazową dla porównań pamięci, należy rozważyć zrobienie migawki na początku sesji debugowania.

6. Uruchom scenariusz, który spowoduje, że pierwszy punkt przerwania zostanie trafiony.

7. Podczas gdy debuger jest wstrzymany w pierwszym punkcie przerwania, wybierz pozycję **Zrób migawkę** na pasku narzędzi podsumowanie **użycia pamięci.**

8. Naciśnij **klawisz F5,** aby uruchomić aplikację do drugiego punktu przerwania.

9. Teraz zrób kolejną migawkę.

     W tym momencie można rozpocząć analizowanie danych.

## <a name="analyze-memory-usage-data"></a>Analizowanie danych użycia pamięci
Wiersze tabeli podsumowania użycia pamięci zawiera listę migawek, które zostały wykonane podczas sesji debugowania i zawiera łącza do bardziej szczegółowych widoków.

![Tabela podsumowania pamięci](../profiling/media/dbgdiag_mem_summarytable.png "DBGDIAG_MEM_SummaryTable")

 Nazwa kolumn zależy od trybu debugowania wybranego we właściwościach projektu: .NET, macierzystym lub mieszanym (zarówno .NET, jak i macierzystym).

- **Kolumny Obiekty (Diff)** i **Alokacje (Diff)** wyświetlają liczbę obiektów w .NET i pamięć natywną podczas robienia migawki.

- Kolumna **Rozmiar sterty (Diff)** wyświetla liczbę bajtów w obszarze .NET i natywne sterty

Po wykonaniu wielu migawek komórki tabeli podsumowania zawierają zmianę wartości między migawką wiersza a poprzednią migawką.

Aby przeanalizować użycie pamięci, kliknij jedno z łączy, które otwiera szczegółowy raport użycia pamięci:

- Aby wyświetlić szczegóły różnicy między bieżącą migawką a poprzednią migawką, wybierz łącze zmiany po lewej stronie strzałki (![Zwiększenie użycia pamięci](../profiling/media/prof-tour-mem-usage-up-arrow.png "Zwiększenie użycia pamięci")). Czerwona strzałka wskazuje wzrost użycia pamięci, a zielona strzałka wskazująca spadek.

> [!TIP]
> Aby ułatwić identyfikowanie problemów z pamięcią, raporty różnicowe są sortowane według typów obiektów, które zwiększyły się najbardziej w ogólnej liczbie (kliknij łącze zmień w kolumnie **Obiekty (Diff)** lub które zwiększyły się najbardziej w ogólnym rozmiarze sterty (kliknij łącze zmień w kolumnie **Rozmiar sterty (Diff).**

- Aby wyświetlić szczegóły tylko wybranej migawki, kliknij łącze bez zmiany.

   Raport pojawi się w osobnym oknie.

### <a name="managed-types-reports"></a>Raporty typów zarządzanych
 Wybierz bieżące łącze komórki **Obiekty (Diff)** lub **Alokacje (Diff)** w tabeli podsumowania Użycie pamięci.

 ![Debuger zarządzanego raportu typu &#45; ścieżki do katalogu głównego](../profiling/media/dbgdiag_mem_managedtypesreport_pathstoroot.png "DBGDIAG_MEM_ManagedTypesReport_PathsToRoot")

 Górne okienko pokazuje liczbę i rozmiar typów w migawce, w tym rozmiar wszystkich obiektów, do których odwołuje się typ **(Rozmiar włącznie).**

 Drzewo **Ścieżki do katalogu głównego** w dolnym okienku wyświetla obiekty odwołują się do typu wybranego w górnym okienku. Moduł odśmiecania pamięci .NET czyści pamięć dla obiektu tylko wtedy, gdy ostatni typ, który odwołuje się do niego został zwolniony.

 Drzewo **Obiekty odniesienia** wyświetla odwołania, które są utrzymywane przez typ wybrany w górnym okienku.

 ![Widok raportu zarządzanych obiektów, do których istnieje odwołanie](../profiling/media/dbgdiag_mem_managedtypesreport_referencedtypes.png "DBGDIAG_MEM_ManagedTypesReport_ReferencedTypes")

 Aby wyświetlić wystąpienia wybranego typu w górnym okienku, wybierz ikonę ![Wystąpienia.](../profiling/media/dbgdiag_mem_instanceicon.png "DBGDIAG_MEM_InstanceIcon")

 ![Widok wystąpień](../profiling/media/dbgdiag_mem_managedtypesreport_instances.png "DBGDIAG_MEM_ManagedTypesReport_Instances")

 Widok **Wystąpienia** wyświetla wystąpienia zaznaczonego obiektu w migawce w górnym okienku. W **okienku Ścieżki do obiektów głównych** i obiektów **przywołytych** wyświetla obiekty odwołują się do zaznaczonego wystąpienia oraz typy, do których odwołuje się wybrane wystąpienie. Po zatrzymaniu debugera w punkcie, w którym zrobiono migawkę, można najechać kursorem na komórkę **Wartość,** aby wyświetlić wartości obiektu w etykietce narzędzia.

### <a name="native-type-reports"></a>Raporty typów natywnych
 Wybierz bieżące łącze komórki **Alokacje (Diff)** lub **Rozmiar sterty (Diff)** w tabeli podsumowania Użycie pamięci w oknie **Narzędzia diagnostyczne.**

 ![Widok typu macierzystego](../profiling/media/dbgdiag_mem_native_typesview.png "DBGDIAG_MEM_Native_TypesView")

 **Widok typów** wyświetla liczbę i rozmiar typów w migawce.

- Wybierz ikonę wystąpień (![Ikona wystąpienia w kolumnie Typ obiektu](../profiling/media/dbg_mma_instancesicon.png "DBG_MMA_InstancesIcon")) wybranego typu, aby wyświetlić informacje o obiektach wybranego typu w migawce.

     W widoku **Wystąpienia** są wyświetlane każde wystąpienie wybranego typu. Wybranie wystąpienia powoduje wyświetlenie stosu wywołań, które spowodowało utworzenie wystąpienia w okienku **Stos wywołań alokacji.**

     ![Widok wystąpień](../profiling/media/dbgdiag_mem_native_instances.png "DBGDIAG_MEM_Native_Instances")

- Wybierz **pozycję Widok stosów** na liście **Tryb widoku,** aby wyświetlić stos alokacji dla wybranego typu.

     ![Widok stosów](../profiling/media/dbgdiag_mem_native_stacksview.png "DBGDIAG_MEM_Native_StacksView")

### <a name="change-diff-reports"></a>Raporty zmian (diff)

- Wybierz łącze zmiany w komórce tabeli podsumowania na karcie **Użycie pamięci** w oknie **Narzędzia diagnostyczne.**

   ![Wybieranie&#41; &#40;zmian](../profiling/media/dbgdiag_mem_choosediffreport.png "DBGDIAG_MEM_ChooseDiffReport")

- Wybierz migawkę na liście **Porównaj z** raportem zarządzanym lub natywnym.

   ![Wybieranie migawki z listy Porównaj do](../profiling/media/dbgdiag_mem_choosecompareto.png "DBGDIAG_MEM_ChooseCompareTo")

Raport zmian dodaje kolumny (oznaczone **(Diff)**) do raportu podstawowego, które pokazują różnicę między wartością migawki podstawowej a migawką porównania. Oto jak może wyglądać raport różnicowy widoku typu macierzystego:

![Widok różnicowych typów natywnych](../profiling/media/dbgdiag_mem_native_typesviewdiff.png "DBGDIAG_MEM_Native_TypesViewDiff")

## <a name="blogs-and-videos"></a>Blogi i filmy

[Analizowanie procesora i pamięci podczas debugowania](https://devblogs.microsoft.com/visualstudio/analyze-cpu-memory-while-debugging/)

[Visual C++ Blog: Profilowanie pamięci w języku Visual C++ 2015](https://devblogs.microsoft.com/cppblog/memory-profiling-in-visual-c-2015/)

## <a name="next-steps"></a>Następne kroki

W tym samouczku dowiesz się, jak zbierać i analizować dane użycia pamięci. Jeśli już ukończyłeś [wycieczkę po profilirze,](../profiling/profiling-feature-tour.md)możesz szybko przyjrzeć się, jak analizować użycie procesora w aplikacjach.

> [!div class="nextstepaction"]
> [Analizowanie użycia procesora](../profiling/beginners-guide-to-performance-profiling.md)
