---
title: Pomiar użycia pamięci w aplikacjach
description: Umożliwia znajdowanie przecieków pamięci i nieefektywne pamięci podczas debugowania za pomocą narzędzia diagnostyczne zintegrowane z debugerem.
ms.custom: seodec18
ms.date: 04/25/2018
ms.topic: tutorial
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: bcb24742a4387a84bba0b52763cdb559280c24c4
ms.sourcegitcommit: 36f5ffd6ae3215fe31837f4366158bf0d871f7a9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59232778"
---
# <a name="measure-memory-usage-in-visual-studio"></a>Użycie pamięci miar w programie Visual Studio

Podczas debugowania za pomocą zintegrowane z debugerem umożliwia znajdowanie przecieków pamięci i pamięci nieefektywne **użycie pamięci** narzędzia diagnostycznego. Narzędzie umożliwia wykorzystanie pamięci, zapoznasz się z co najmniej jeden *migawek* sterty pamięci zarządzanego i natywnego ułatwi zrozumienie wpływu użycia pamięci typów obiektów. Można zbierać migawki .NET, Tryb natywny lub mieszany (.NET i natywny) aplikacji.

Pokazano grafiki **narzędzia diagnostyczne** okna (dostępne w programie Visual Studio 2015 Update 1 lub nowszy):

![DiagnosticTools&#45;Update1](../profiling/media/diagnostictools-update1.png "DiagnosticTools-Update1")

Mimo że można zbierać migawki pamięci w dowolnym momencie **użycie pamięci** narzędzie debugera programu Visual Studio można użyć do kontrolowania, jak aplikacja wykonuje podczas badania problemów z wydajnością. Ustawianie punktów przerwania, przechodzenie krok po kroku, Przerwij wszystko i inne akcje debuger może pomóc w skoncentrowaniu swoje badania wydajności ścieżki kodu, które są najbardziej odpowiednie. Wykonywania tych akcji, gdy aplikacja jest uruchomiona, można wyeliminować szumu od kodu, który nie interesują użytkownika i może znacznie skrócić czas potrzebny do zdiagnozowania problemu.

Można również użyć narzędzia pamięci poza debugerem. Zobacz [użycie pamięci bez debugowania](../profiling/memory-usage-without-debugging2.md). Można użyć narzędzi profilowania nie załączonym debuggerze, system Windows 7 lub nowszy. Windows 8 lub nowszy jest wymagany do uruchamiania narzędzi profilowania z debugerem (**narzędzia diagnostyczne** okno).

> [!NOTE]
> **Niestandardowe obsługi alokatora** profiler pamięci natywnej polega na zbieraniu alokacji [ETW](/windows-hardware/drivers/devtest/event-tracing-for-windows--etw-) dane zdarzenia wyemitowane przez w czasie wykonywania.  Puli buforów w CRT i zestaw Windows SDK ma została oznaczona na poziomie źródła przechwycić swoje dane alokacji.  Jeśli piszesz własnego puli buforów, a następnie wszystkie funkcje, które zwracają wskaźnik do nowo przydzielonego stosu pamięci może być dekorowane za pomocą [__declspec](/cpp/cpp/declspec)(alokatora), jak pokazano w następującym przykładzie myMalloc:
>
> `__declspec(allocator) void* myMalloc(size_t size)`

W tym samouczku wykonasz następujące czynności:

> [!div class="checklist"]
> * Wykonywanie migawek pamięci
> * Analizowanie danych użycia pamięci

## <a name="collect-memory-usage-data"></a>Zbieranie danych użycia pamięci

1.  Otwórz projekt, który chcesz debugować w programie Visual Studio i ustaw punkt przerwania w swojej aplikacji w punkcie, w którym chcesz rozpocząć badanie użycia pamięci.

    Jeśli masz obszar, w którym podejrzewasz problem pamięci, należy ustawić pierwszy punkt przerwania przed wystąpieniem problemu pamięci.

    > [!TIP]
    >  Ponieważ może stanowić wyzwanie do przechwytywania profilu pamięci operacji, która Cię interesuje, gdy aplikacja często przydziela i zwalnia pamięć, ustawić punkty przerwania na początku i końca operacji (lub wykonać krok po kroku) aby znaleźć konkretny punkt Pamięć zmieniła się.

2.  Ustaw drugi punkt przerwania na końcu funkcji lub regionu kod, który chcesz analizować (lub po wystąpieniu problemu podejrzanych pamięci).

3.  **Narzędzia diagnostyczne** okno pojawia się automatycznie, o ile nie została ona wyłączona. Aby wyświetlić okno ponownie, kliknij przycisk **debugowania** > **Windows** > **Pokaż narzędzia diagnostyczne**.

4.  Wybierz **użycie pamięci** z **wybierz narzędzia** ustawienie na pasku narzędzi.

     ![Pokaż narzędzia diagnostyczne](../profiling/media/diag-tools-select-tool-2.png "DiagToolsSelectTool")

5.  Kliknij przycisk **debugowania / uruchamiania debugowania** (lub **Start** na pasku narzędzi lub **F5**).

     Po zakończeniu ładowania aplikacji zostanie wyświetlony widok podsumowania narzędzia diagnostyczne.

     ![Karta Podsumowanie narzędzia do diagnostyki](../profiling/media/diag-tools-summary-tab-2.png "DiagToolsSummaryTab")

     > [!NOTE]
     >  Ponieważ zbieranie danych może mieć wpływ na wydajność debugowania aplikacji natywnej lub trybu mieszanego pamięci, migawki pamięci są domyślnie wyłączone. Aby włączyć migawek w aplikacji natywnej lub trybu mieszanego, Rozpocznij sesję debugowania (klawisz skrótu: **F5**). Gdy **narzędzia diagnostyczne** zostanie wyświetlone okno, wybierz **użycie pamięci** kartę, a następnie wybierz **profilowanie sterty**.
     >
     >  ![Włącz migawki](../profiling/media/dbgdiag_mem_mixedtoolbar_enablesnapshot.png "DBGDIAG_MEM_MixedToolbar_EnableSnapshot")
     >
     >  Zatrzymaj (klawisz skrótu: **Przenieś**+**F5**) i uruchom ponownie debugowanie.

6.  Aby zrobić migawkę podczas uruchamiania sesji debugowania, wybierz opcję **wykonaj migawkę** na **użycie pamięci** paska narzędzi. (Pomocne może być Ustaw punkt przerwania w tym miejscu także.)

    ![Wykonaj migawkę](../profiling/media/dbgdiag_mem_mixedtoolbar_takesnapshot.png "DBGDIAG_MEM_MixedToolbar_TakeSnapshot")

     > [!TIP]
     >  Aby utworzyć punkt odniesienia dla porównania pamięci, należy rozważyć wykonanie migawki podczas uruchamiania sesji debugowania.

6.  Uruchom scenariusz, który spowoduje, że pierwszy punkt przerwania na.

7.  Gdy debuger jest wstrzymana w pierwszym punkcie przerwania, wybierz **wykonaj migawkę** na **użycie pamięci** paska narzędzi.

8.  Naciśnij klawisz **F5** do uruchomienia aplikacji na drugi punkt przerwania.

9.  Teraz Utwórz kolejną migawkę.

     W tym momencie można rozpocząć analizy danych.

## <a name="analyze-memory-usage-data"></a>Analizowanie danych użycia pamięci
Wiersze tabeli podsumowania użycia pamięci zawiera listę migawek, które miały podczas sesji debugowania i zawiera łącza do bardziej szczegółowych widoków.

![Tabela podsumowująca pamięci](../profiling/media/dbgdiag_mem_summarytable.png "DBGDIAG_MEM_SummaryTable")

 Nazwa kolumny zależą od trybu debugowania, możesz wybrać we właściwościach projektu: .NET, natywny lub mieszany (.NET i natywny).

-   **Obiekty (różnica)** i **alokacje (różnica)** kolumn wyświetlany liczbę obiektów w .NET i pamięci natywnej, gdy migawka została utworzona.

-   **Rozmiar sterty (różnica)** kolumnie jest wyświetlana liczba bajtów w .NET i natywnej sterty

Po wykonaniu wiele migawek komórek tabeli podsumowania obejmują zmianę wartości między migawką wiersza i poprzednią migawkę.

Aby Analizowanie użycia pamięci, kliknij jedno z łączy, które otwiera szczegółowy raport użycia pamięci:

- Aby wyświetlić szczegóły różnicę między bieżącą migawką i poprzedniej migawki, wybierz łącze Zmień strzałkę po lewej stronie (![zwiększyć użycie pamięci](../profiling/media/prof-tour-mem-usage-up-arrow.png "zwiększyć użycie pamięci")). Czerwona strzałka wskazuje wzrost użycia pamięci i zieloną strzałkę, aby wskazuje zmniejszenie.

> [!TIP]
> Aby zidentyfikować problemy z pamięcią szybciej, raporty różnice są sortowane według typów obiektów, które zwiększył się wykorzystać w ogólny numer (kliknij łącze Zmień w **obiekty (różnica)** kolumny) lub większa wykorzystać w ogólny rozmiar sterty (kliknij Zmień łącze w **Rozmiar sterty (różnica)** kolumny).

- Aby wyświetlić szczegóły wybranej migawki, kliknij łącze nie został zmieniony.

   Raport jest wyświetlany w osobnym oknie.

### <a name="managed-types-reports"></a>Zarządzane typy raportów
 Wybierz link bieżącego **obiekty (różnica)** lub **alokacje (różnica)** komórka w tabeli podsumowania użycia pamięci.

 ![Raport typu zarządzanego debugera &#45; ścieżki do obiektu głównego](../profiling/media/dbgdiag_mem_managedtypesreport_pathstoroot.png "DBGDIAG_MEM_ManagedTypesReport_PathsToRoot")

 Górne okienko pokazuje liczbę i rozmiar typów w migawce, takich jak rozmiar wszystkich obiektów, które są przywoływane przez typ (**rozmiarze włącznie**).

 **Ścieżki do obiektu głównego** drzewa w dolnym okienku Wyświetla obiekty odwołujące się do typu wybranego w górnym okienku. Moduł zbierający elementy bezużyteczne .NET Framework Czyści pamięć dla obiektu, tylko wtedy, gdy ostatni typ, który odwołuje się do niej po udostępnieniu.

 **Przywoływane typy** drzewa Wyświetla odwołania, które są przechowywane w wybranego w górnym okienku typu.

 ![Widok raportu z typami zarządzanymi odwołania](../profiling/media/dbgdiag_mem_managedtypesreport_referencedtypes.png "DBGDIAG_MEM_ManagedTypesReport_ReferencedTypes")

 Aby wyświetlić wystąpienia typu wybranego w górnym okienku, wybierz ![ikonę wystąpienia](../profiling/media/dbgdiag_mem_instanceicon.png "DBGDIAG_MEM_InstanceIcon") ikony.

 ![Wystąpienia widoku](../profiling/media/dbgdiag_mem_managedtypesreport_instances.png "DBGDIAG_MEM_ManagedTypesReport_Instances")

 **Wystąpień** widoku wystąpienia wybranego obiektu są wyświetlane w migawce w górnym okienku. **Ścieżki do obiektu głównego** i **przywoływane obiekty** okienku są wyświetlane obiekty odwołujące się do wybranego wystąpienia i typy, które odwołuje się do wybranego wystąpienia. Po zatrzymaniu debugera w punkcie, w którym migawka została utworzona, możesz umieścić kursor **wartość** komórkę, aby wyświetlić wartości obiektów w etykietce narzędzia.

### <a name="native-type-reports"></a>Raporty w typie natywnym
 Wybierz link bieżącego **alokacje (różnica)** lub **Rozmiar sterty (różnica)** komórka w tabeli podsumowania użycia pamięci w **narzędzia diagnostyczne** okna.

 ![Widok typu natywnego](../profiling/media/dbgdiag_mem_native_typesview.png "DBGDIAG_MEM_Native_TypesView")

 **Widok typów** Wyświetla liczbę i rozmiar typów w migawce.

-   Wybierz ikonę wystąpienia (![ikonę wystąpienia, w kolumnie Typ obiektu](../profiling/media/dbg_mma_instancesicon.png "DBG_MMA_InstancesIcon")) dla wybranego typu, aby wyświetlić informacje o obiektach wybranego typu w migawce.

     **Wystąpień** widok zawiera każde wystąpienie wybranego typu. Wybranie wystąpienia przedstawia stos wywołań, które spowodowało utworzenie wystąpienia w **stos wywołań alokacji** okienka.

     ![Wystąpienia widoku](../profiling/media/dbgdiag_mem_native_instances.png "DBGDIAG_MEM_Native_Instances")

-   Wybierz **widok stosów** w **tryb widoku** listy w celu wyświetlenia alokacji stosu dla wybranego typu.

     ![Widok stosów](../profiling/media/dbgdiag_mem_native_stacksview.png "DBGDIAG_MEM_Native_StacksView")

### <a name="change-diff-reports"></a>Zmiany raportów (różnica)

- Wybierz łącze zmian w komórce tabeli podsumowania **użycie pamięci** karcie **narzędzia diagnostyczne** okna.

   ![Kliknij przycisk Zmień &#40;diff&#41; raportu](../profiling/media/dbgdiag_mem_choosediffreport.png "DBGDIAG_MEM_ChooseDiffReport")

- Wybierz migawkę w **Porównaj z** raport zarządzane lub natywne listy.

   ![Wybierz migawkę z porównania na liście](../profiling/media/dbgdiag_mem_choosecompareto.png "DBGDIAG_MEM_ChooseCompareTo")

Raport zmiana dodaje kolumn (oznaczone **(różnica)**) do podstawowej raport, który wyświetlenie różnicy między wartością podstawowy, migawki i migawki porównania. Poniżej przedstawiono, jak może wyglądać raport natywnego typu widoku różnic:

![Typy natywne widoku różnic](../profiling/media/dbgdiag_mem_native_typesviewdiff.png "DBGDIAG_MEM_Native_TypesViewDiff")

## <a name="blogs-and-videos"></a>Blogi i filmy wideo

[Analizowanie użycia Procesora i pamięci podczas debugowania](https://devblogs.microsoft.com/visualstudio/analyze-cpu-memory-while-debugging/)

[Visual C++ Blog: Profilowanie pamięci w programie Visual C++ 2015](https://devblogs.microsoft.com/cppblog/memory-profiling-in-visual-c-2015/)

## <a name="next-steps"></a>Następne kroki

W tym samouczku wyjaśniono sposób zbieranie i analizowanie danych użycia pamięci. Jeśli znasz już [samouczek programu profilującego](../profiling/profiling-feature-tour.md), możesz chcieć uzyskać krótkie omówienie sposobu analizowania użycia procesora CPU w twoich aplikacjach.

> [!div class="nextstepaction"]
> [Analizowanie użycia procesora CPU](../profiling/beginners-guide-to-performance-profiling.md)
