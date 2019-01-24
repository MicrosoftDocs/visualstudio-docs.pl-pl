---
title: Użycie pamięci | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: bbb58d6c-3362-4ca3-8e87-64b2d4415bf6
caps.latest.revision: 17
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 6b060f35abf79d76e17f847e6b4b296c253a4b30
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54766120"
---
# <a name="memory-usage"></a>Użycie pamięci
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Podczas debugowania za pomocą zintegrowane z debugerem umożliwia znajdowanie przecieków pamięci i pamięci nieefektywne **użycie pamięci** narzędzia diagnostycznego. Narzędzie umożliwia wykorzystanie pamięci, zapoznasz się z co najmniej jeden *migawek* sterty pamięci zarządzanego i natywnego. Można zbierać migawki .NET, Tryb natywny lub mieszany (.NET i natywny) aplikacji.  
  
- Możesz analizować pojedynczej migawki zrozumieć konsekwencje typów obiektów na wykorzystanie pamięci i znaleźć kod w swojej aplikacji, która używa pamięci nieefektywne.  
  
- Można również porównać (różnica) dwiema migawkami znajdowanie obszarów w kodzie aplikacji, które powodują wykorzystanie pamięci zwiększyć wraz z upływem czasu.  
  
  Pokazano grafiki **narzędzia diagnostyczne** okna w Visual Studio 2015 Update 1:  
  
  ![DiagnosticTools&#45;Update1](../profiling/media/diagnostictools-update1.png "DiagnosticTools-Update1")  
  
  Mimo że można zbierać migawki pamięci w dowolnym momencie **użycie pamięci** narzędzie debugera programu Visual Studio można użyć do kontrolowania, jak aplikacja wykonuje podczas badania problemów z wydajnością. Ustawianie punktów przerwania, przechodzenie krok po kroku, Przerwij wszystko i inne akcje debuger może pomóc w skoncentrowaniu swoje badania wydajności ścieżki kodu, które są najbardziej odpowiednie. Wykonanie tych akcji, gdy Twoja aplikacja jest uruchomiona można eliminuje szumu od kodu, który nie interesują użytkownika i może znacznie skrócić czas potrzebny do zdiagnozowania problemu.  
  
  Można również użyć narzędzia pamięci poza debugerem. Zobacz [użycie pamięci bez debugowania](http://msdn.microsoft.com/library/8883bc5f-df86-4f84-aa2b-a21150f499b0).  
  
> [!NOTE]
>  **Niestandardowe obsługi alokatora** profiler pamięci natywnej polega na zbieraniu alokacji [ETW](https://msdn.microsoft.com/library/windows/desktop/bb968803\(v=vs.85\).aspx) dane zdarzenia wyemitowane przez w czasie wykonywania.  Puli buforów w CRT i zestaw Windows SDK ma została oznaczona na poziomie źródła przechwycić swoje dane alokacji.  Jeśli piszesz własnego buforów niż wszystkie funkcje, które zwracają wskaźnik do nowo przydzielonego stosu pamięci może być dekorowane za pomocą [__declspec](http://msdn.microsoft.com/library/832db681-e8e1-41ca-b78c-cd9d265cdb87)(alokatora), jak pokazano w następującym przykładzie myMalloc:  
>   
>  `__declspec(allocator) void* myMalloc(size_t size)`  
  
## <a name="analyze-memory-use-with-the-debugger"></a>Analiza użycia pamięci za pomocą debugera  
  
> [!NOTE]
>  Ponieważ zbieranie danych może mieć wpływ na wydajność debugowania aplikacji natywnej lub trybu mieszanego pamięci, migawki pamięci są domyślnie wyłączone. Aby włączyć migawek aplikacje natywne lub trybu mieszanego, Rozpocznij sesję debugowania (klawisz skrótu: **F5**). Gdy **narzędzia diagnostyczne** zostanie wyświetlone okno, wybierz kartę użycie pamięci, a następnie wybierz **Włącz migawki**.  
>   
>  ![Włącz migawki](../profiling/media/dbgdiag-mem-mixedtoolbar-enablesnapshot.png "DBGDIAG_MEM_MixedToolbar_EnableSnapshot")  
>   
>  Zatrzymaj (klawisz skrótu: **SHIFT + F5**) i uruchom ponownie debugowanie.  
  
 Zawsze, gdy chcesz przechwytywać stan pamięci, wybierać **wykonaj migawkę** na **użycie pamięci** paska narzędzi.  
  
 ![Wykonaj migawkę](../profiling/media/dbgdiag-mem-mixedtoolbar-takesnapshot.png "DBGDIAG_MEM_MixedToolbar_TakeSnapshot")  
  
> [!TIP]
> - Aby utworzyć punkt odniesienia dla porównania pamięci, należy rozważyć wykonanie migawki podczas uruchamiania sesji debugowania.  
>   -   Ponieważ może stanowić wyzwanie do przechwytywania profilu pamięci operacji, która Cię interesuje, gdy aplikacja często przydziela i zwalnia pamięć, ustawianie punktów przerwania na początku i końca operacji lub krok za pomocą operacji, aby znaleźć konkretny punkt Pamięć zmieniła się.  
  
## <a name="viewing-memory-snapshot-details"></a>Wyświetlanie szczegółów migawki pamięci  
 Wiersze tabeli podsumowania użycia pamięci zawiera listę migawek, które miały podczas sesji debugowania.  
  
 Kolumn w wierszu zależą od trybu debugowania, możesz wybrać we właściwościach projektu: .NET, natywny lub mieszany (.NET i natywny).  
  
- **Zarządzanego obiektu**s i **natywnych alokacje** kolumn wyświetlany liczbę obiektów w .NET i pamięci natywnej, gdy migawka została utworzona.  
  
- **Zarządzane Rozmiar sterty** i **Rozmiar sterty natywnej** liczbę bajtów w kolumnach są wyświetlane w .NET i natywnej sterty  
  
- Po wykonaniu wiele migawek komórek tabeli podsumowania obejmują zmianę wartości między migawką wiersza i poprzednią migawkę.  
  
   ![Komórki tabeli podsumowania pamięci](../profiling/media/dbgdiag-mem-summarytablecell.png "DBGDIAG_MEM_SummaryTableCell")  
  
  **Aby wyświetlić raport o szczegółach:**  
  
- Aby wyświetlić szczegóły wybranej migawki, wybierz bieżące połączenie.  
  
- Aby wyświetlić szczegóły różnicę między bieżącą migawką i poprzedniej migawki, wybierz łącze zmian.  
  
  Raport jest wyświetlany w osobnym oknie.  
  
## <a name="memory-usage-details-reports"></a>Raporty ze szczegółami użycia pamięci  
  
### <a name="managed-types-reports"></a>Zarządzane typy raportów  
 Wybierz link bieżącego **obiekty zarządzane** lub **zarządzane Rozmiar sterty** komórka w tabeli podsumowania użycia pamięci.  
  
 ![Raport typu zarządzanego debugera &#45; ścieżki do obiektu głównego](../profiling/media/dbgdiag-mem-managedtypesreport-pathstoroot.png "DBGDIAG_MEM_ManagedTypesReport_PathsToRoot")  
  
 Górne okienko pokazuje liczbę i rozmiar typów w migawce, takich jak rozmiar wszystkich obiektów, które są przywoływane przez typ (**rozmiarze włącznie**).  
  
 **Ścieżki do obiektu głównego** drzewa w dolnym okienku Wyświetla obiekty odwołujące się do typu wybranego w górnym okienku. Moduł zbierający elementy bezużyteczne .NET Framework Czyści pamięć dla obiektu, tylko wtedy, gdy ostatni typ, który odwołuje się do niej po udostępnieniu.  
  
 **Przywoływane typy** drzewa Wyświetla odwołania, które są przechowywane w wybranego w górnym okienku typu.  
  
 ![Zarządzane eferenced typów widoku raportu](../profiling/media/dbgdiag-mem-managedtypesreport-referencedtypes.png "DBGDIAG_MEM_ManagedTypesReport_ReferencedTypes")  
  
 Aby wyświetlić wystąpienia typu wybranego w górnym okienku, wybierz ![ikonę wystąpienia](../profiling/media/dbgdiag-mem-instanceicon.png "DBGDIAG_MEM_InstanceIcon") ikony.  
  
 ![Wystąpienia widoku](../profiling/media/dbgdiag-mem-managedtypesreport-instances.png "DBGDIAG_MEM_ManagedTypesReport_Instances")  
  
 **Wystąpień** widoku wystąpienia wybranego obiektu są wyświetlane w migawce w górnym okienku. Ścieżki do katalogu głównego i obiekty, do których odwołuje się okienka Wyświetl obiekty odwołujące się do wybranego wystąpienia i typy, które odwołuje się do wybranego wystąpienia. Po zatrzymaniu debugera w punkcie, w którym migawka została utworzona, możesz umieścić kursor komórkę wartość, aby wyświetlić wartości obiektów w etykietce narzędzia.  
  
### <a name="native-type-reports"></a>Raporty w typie natywnym  
 Wybierz bieżące połączenie z **natywnych alokacje** lub **Rozmiar sterty natywnej** komórka w tabeli podsumowania użycia pamięci w **narzędzia diagnostyczne** okna.  
  
 ![Widok typu natywnego](../profiling/media/dbgdiag-mem-native-typesview.png "DBGDIAG_MEM_Native_TypesView")  
  
 **Widok typów** Wyświetla liczbę i rozmiar typów w migawce.  
  
-   Wybierz ikonę wystąpienia (![ikonę wystąpienia, w kolumnie Typ obiektu](../misc/media/dbg-mma-instancesicon.png "DBG_MMA_InstancesIcon")) dla wybranego typu, aby wyświetlić informacje o obiektach wybranego typu w migawce.  
  
     **Wystąpień** widok zawiera każde wystąpienie wybranego typu. Wybranie wystąpienia przedstawia stos wywołań, które spowodowało utworzenie wystąpienia w **stos wywołań alokacji** okienka.  
  
     ![Wystąpienia widoku](../profiling/media/dbgdiag-mem-native-instances.png "DBGDIAG_MEM_Native_Instances")  
  
-   Wybierz **widok stosów** w **tryb widoku** listy w celu wyświetlenia alokacji stosu dla wybranego typu.  
  
     ![Widok stosów](../profiling/media/dbgdiag-mem-native-stacksview.png "DBGDIAG_MEM_Native_StacksView")  
  
### <a name="change-diff-reports"></a>Zmiany raportów (różnica)  
  
- Wybierz łącze zmian w komórce tabeli podsumowania **użycie pamięci** karcie **narzędzia diagnostyczne** okna.  
  
   ![Kliknij przycisk Zmień &#40;dif&#41;raportu f](../profiling/media/dbgdiag-mem-choosediffreport.png "DBGDIAG_MEM_ChooseDiffReport")  
  
- Wybierz migawkę w **Porównaj z** raport zarządzane lub natywne listy.  
  
   ![Wybierz migawkę z porównania na liście](../profiling/media/dbgdiag-mem-choosecompareto.png "DBGDIAG_MEM_ChooseCompareTo")  
  
  Raport zmiana dodaje kolumn (oznaczone **(różnica)**) do podstawowej raport, który wyświetlenie różnicy między wartością podstawowy, migawki i migawki porównania. Poniżej przedstawiono, jak może wyglądać raport natywnego typu widoku różnic:  
  
  ![Typy natywne Diff Veiw](../profiling/media/dbgdiag-mem-native-typesviewdiff.png "DBGDIAG_MEM_Native_TypesViewDiff")  
  
## <a name="blogs-and-videos"></a>Blogi i filmy wideo  
 [Okno debugera narzędzia diagnostyczne w programie Visual Studio 2015](http://blogs.msdn.com/b/visualstudioalm/archive/2015/01/16/diagnostic-tools-debugger-window-in-visual-studio-2015.aspx)  
  
 [Blog: Narzędzie użycie pamięci podczas debugowania w programie Visual Studio 2015](http://blogs.msdn.com/b/visualstudioalm/archive/2014/11/13/memory-usage-tool-while-debugging-in-visual-studio-2015.aspx)  
  
 [Blogu Visual C++: Diagnostyka pamięci natywnej w programie VS2015 (wersja zapoznawcza)](http://blogs.msdn.com/b/vcblog/archive/2014/11/21/native-memory-diagnostics-in-vs2015-preview.aspx)  
  
 [Blogu Visual C++: Pamięć natywna narzędzia diagnostyczne Visual Studio 2015 CTP](http://blogs.msdn.com/b/vcblog/archive/2014/06/04/native-memory-diagnostic-tools-for-visual-studio-14-ctp1.aspx)
