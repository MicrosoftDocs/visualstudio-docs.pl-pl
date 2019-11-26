---
title: Użycie pamięci | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: bbb58d6c-3362-4ca3-8e87-64b2d4415bf6
caps.latest.revision: 17
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 0feabad8dfa3b086c9ed5a1a58e231719774f9cc
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2019
ms.locfileid: "74298367"
---
# <a name="memory-usage"></a>Użycie pamięci
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Znajdowanie przecieków pamięci i niewydajnej pamięci podczas debugowania za pomocą narzędzia diagnostycznego **dotyczącego użycia pamięci** zintegrowanej z debugerem. Narzędzie użycie pamięci umożliwia wykonanie co najmniej jednej *migawki* zarządzanego i natywnego sterty pamięci. Można zbierać migawki .NET, Tryb natywny lub mieszany (.NET i natywny) aplikacji.  
  
- Możesz analizować pojedynczej migawki zrozumieć konsekwencje typów obiektów na wykorzystanie pamięci i znaleźć kod w swojej aplikacji, która używa pamięci nieefektywne.  
  
- Można również porównać (różnica) dwiema migawkami znajdowanie obszarów w kodzie aplikacji, które powodują wykorzystanie pamięci zwiększyć wraz z upływem czasu.  
  
  Na poniższej ilustracji przedstawiono okno **Narzędzia diagnostyczne** w programie Visual Studio 2015 Update 1:  
  
  ![DiagnosticTools&#45;Update1](../profiling/media/diagnostictools-update1.png "DiagnosticTools — Update1")  
  
  Chociaż w dowolnym momencie można zbierać migawki pamięci w narzędziu **użycie pamięci** , można użyć debugera programu Visual Studio, aby kontrolować sposób wykonywania aplikacji podczas badania problemów z wydajnością. Ustawianie punktów przerwania, przechodzenie krok po kroku, Przerwij wszystko i inne akcje debuger może pomóc w skoncentrowaniu swoje badania wydajności ścieżki kodu, które są najbardziej odpowiednie. Wykonywanie tych akcji, gdy aplikacja jest uruchomiona, może wyeliminować hałas z kodu, który nie jest interesujący, i może znacząco skrócić czas, w którym można zdiagnozować problem.  
  
  Można również użyć narzędzia pamięci poza debugerem. Zobacz [użycie pamięci bez debugowania](https://msdn.microsoft.com/library/8883bc5f-df86-4f84-aa2b-a21150f499b0).  
  
> [!NOTE]
> **Obsługa alokatora niestandardowego** Profiler pamięci natywnej działa przez zbieranie danych zdarzeń [ETW](https://msdn.microsoft.com/library/windows/desktop/bb968803\(v=vs.85\).aspx) alokacji emitowanych przez środowisko uruchomieniowe.  Puli buforów w CRT i zestaw Windows SDK ma została oznaczona na poziomie źródła przechwycić swoje dane alokacji.  Jeśli piszesz własne przydziały, niż wszystkie funkcje, które zwracają wskaźnik do nowo przydzieloną pamięci sterty, mogą mieć [__declspec](https://msdn.microsoft.com/library/832db681-e8e1-41ca-b78c-cd9d265cdb87)(Alokator), jak pokazano w tym przykładzie dla elementu malloc:  
>   
> `__declspec(allocator) void* myMalloc(size_t size)`  
  
## <a name="analyze-memory-use-with-the-debugger"></a>Analizowanie użycia pamięci za pomocą debugera  
  
> [!NOTE]
> Ponieważ zbieranie danych może mieć wpływ na wydajność debugowania aplikacji natywnej lub trybu mieszanego pamięci, migawki pamięci są domyślnie wyłączone. Aby włączyć migawki aplikacji w trybie macierzystym lub mieszanym, uruchom sesję debugowania (klawisz skrótu: **F5**). Po wyświetleniu okna **Narzędzia diagnostyczne** wybierz kartę użycie pamięci, a następnie wybierz pozycję **Włącz migawki**.  
>   
> ![Włącz migawki](../profiling/media/dbgdiag-mem-mixedtoolbar-enablesnapshot.png "DBGDIAG_MEM_MixedToolbar_EnableSnapshot")  
>   
> Zatrzymaj (klawisz skrótu: **Shift + F5**) i uruchom ponownie debugowanie.  
  
 W każdym przypadku, gdy chcesz przechwytywać stan pamięci, wybierz pozycję **zrób migawkę** na pasku narzędzi podsumowanie **użycia pamięci** .  
  
 ![Utwórz migawkę](../profiling/media/dbgdiag-mem-mixedtoolbar-takesnapshot.png "DBGDIAG_MEM_MixedToolbar_TakeSnapshot")  
  
> [!TIP]
> - Aby utworzyć punkt odniesienia dla porównania pamięci, należy rozważyć wykonanie migawki podczas uruchamiania sesji debugowania.  
>   - Ponieważ może być trudne do przechwycenia profilu pamięci operacji, która interesuje Cię, gdy aplikacja często przydziela i cofa alokację pamięci, ustaw punkty przerwania na początku i na końcu operacji lub przechodząc przez operację, aby znaleźć dokładny punkt pamięć zmieniła się.  
  
## <a name="viewing-memory-snapshot-details"></a>Wyświetlanie szczegółów migawek pamięci  
 W tabeli podsumowania użycia pamięci wymieniono migawki, które zostały wykonane podczas sesji debugowania.  
  
 Kolumny wiersza zależą od trybu debugowania wybranego we właściwościach projektu: .NET, native lub Mixed (zarówno .NET, jak i Native).  
  
- Kolumny **zarządzane**obiekty i **natywne alokacje** wyświetlają liczbę obiektów w .NET i pamięci natywnej podczas tworzenia migawki.  
  
- Kolumny **rozmiar sterty zarządzanej** i **rozmiar sterty natywnej** wyświetlają liczbę bajtów w stercie .NET i natywnych stert  
  
- Po wykonaniu wiele migawek komórek tabeli podsumowania obejmują zmianę wartości między migawką wiersza i poprzednią migawkę.  
  
   ![Komórka tabeli podsumowania pamięci](../profiling/media/dbgdiag-mem-summarytablecell.png "DBGDIAG_MEM_SummaryTableCell")  
  
  **Aby wyświetlić szczegółowy raport:**  
  
- Aby wyświetlić szczegóły tylko wybranej migawki, wybierz bieżące łącze.  
  
- Aby wyświetlić szczegóły różnicy między bieżącą migawką i poprzednią migawką, wybierz łącze Zmień.  
  
  Raport jest wyświetlany w osobnym oknie.  
  
## <a name="memory-usage-details-reports"></a>Raporty szczegółów użycia pamięci  
  
### <a name="managed-types-reports"></a>Zarządzane typy raportów  
 Wybierz bieżące łącze do komórki **Managed Objects** lub **rozmiaru sterty zarządzanej** w tabeli Podsumowanie użycia pamięci.  
  
 ![Debugowanie ścieżki raportów &#45; typów zarządzanych do katalogu głównego](../profiling/media/dbgdiag-mem-managedtypesreport-pathstoroot.png "DBGDIAG_MEM_ManagedTypesReport_PathsToRoot")  
  
 Górne okienko pokazuje liczbę i rozmiar typów w migawce, w tym rozmiar wszystkich obiektów, do których odwołuje się typ (**rozmiar włącznie**).  
  
 **Ścieżki do drzewa głównego** w dolnym okienku wyświetla obiekty odwołujące się do typu wybranego w górnym okienku. Moduł zbierający elementy bezużyteczne .NET Framework Czyści pamięć dla obiektu, tylko wtedy, gdy ostatni typ, który odwołuje się do niej po udostępnieniu.  
  
 Drzewo **typów, do których** istnieją odwołania, zawiera odwołania, które są przechowywane przez typ wybrany w górnym okienku.  
  
 ![Widok raportu typów zarządzanych eferenced](../profiling/media/dbgdiag-mem-managedtypesreport-referencedtypes.png "DBGDIAG_MEM_ManagedTypesReport_ReferencedTypes")  
  
 Aby wyświetlić wystąpienia wybranego typu w górnym okienku, wybierz ikonę ![wystąpienia](../profiling/media/dbgdiag-mem-instanceicon.png "DBGDIAG_MEM_InstanceIcon") ikona.  
  
 ![Widok wystąpień](../profiling/media/dbgdiag-mem-managedtypesreport-instances.png "DBGDIAG_MEM_ManagedTypesReport_Instances")  
  
 Widok **wystąpienia** wyświetla wystąpienia wybranego obiektu w migawce w górnym okienku. Okienko ścieżki do katalogu głównego i przywoływanych obiektów wyświetla obiekty odwołujące się do wybranego wystąpienia i typy, do których odwołuje się wybrane wystąpienie. Gdy debuger zostanie zatrzymany w punkcie, w którym zrobiono migawkę, możesz umieścić wskaźnik myszy nad komórką wartości, aby wyświetlić wartości obiektu w etykietce narzędzia.  
  
### <a name="native-type-reports"></a>Raporty w typie natywnym  
 Wybierz bieżące łącze **natywnej** lub natywnej komórki **rozmiaru sterty** w tabeli podsumowania użycia pamięci okna **Narzędzia diagnostyczne** .  
  
 ![Widok typu natywnego](../profiling/media/dbgdiag-mem-native-typesview.png "DBGDIAG_MEM_Native_TypesView")  
  
 **Widok typy** wyświetla liczbę i rozmiar typów w migawce.  
  
- Wybierz ikonę wystąpienia (![ikona wystąpienia w kolumnie Typ obiektu](../misc/media/dbg-mma-instancesicon.png "DBG_MMA_InstancesIcon")) wybranego typu, aby wyświetlić informacje o obiektach wybranego typu w migawce.  
  
     Widok **wystąpienia** wyświetla każde wystąpienie wybranego typu. Wybranie wystąpienia powoduje wyświetlenie stosu wywołań, który spowodowało utworzenie wystąpienia w okienku **stosu wywołań alokacji** .  
  
     ![Widok wystąpień](../profiling/media/dbgdiag-mem-native-instances.png "DBGDIAG_MEM_Native_Instances")  
  
- Wybierz **Widok stosów** na liście **tryb wyświetlania** , aby wyświetlić stos alokacji dla wybranego typu.  
  
     ![Widok stosów](../profiling/media/dbgdiag-mem-native-stacksview.png "DBGDIAG_MEM_Native_StacksView")  
  
### <a name="change-diff-reports"></a>Zmiany raportów (różnica)  
  
- Wybierz łącze Zmień w komórce tabeli podsumowującej karty **użycie pamięci** w oknie **Narzędzia diagnostyczne** .  
  
   ![Wybieranie zmiany &#40;w raporcie&#41;DIF f](../profiling/media/dbgdiag-mem-choosediffreport.png "DBGDIAG_MEM_ChooseDiffReport")  
  
- Wybierz migawkę na liście **Porównaj z** w raporcie zarządzanym lub natywnym.  
  
   ![Wybierz migawkę z listy Porównaj z](../profiling/media/dbgdiag-mem-choosecompareto.png "DBGDIAG_MEM_ChooseCompareTo")  
  
  Raport zmiana dodaje kolumny (oznaczone atrybutem **(diff)** ) do raportu podstawowego, który pokazuje różnicę między podstawową wartością migawki a migawką porównania. Oto jak wygląda raport różnicowy widoku typu natywnego:  
  
  ![Typy natywne diff veiw](../profiling/media/dbgdiag-mem-native-typesviewdiff.png "DBGDIAG_MEM_Native_TypesViewDiff")  
  
## <a name="blogs-and-videos"></a>Blogi i filmy wideo  
 [Okno debugera narzędzia diagnostyczne w programie Visual Studio 2015](https://devblogs.microsoft.com/devops/diagnostic-tools-debugger-window-in-visual-studio-2015/)  
  
 [Blog: Narzędzie użycie pamięci podczas debugowania w programie Visual Studio 2015](https://devblogs.microsoft.com/devops/memory-usage-tool-while-debugging-in-visual-studio-2015/)  
  
 [Blog C++ wizualny: Diagnostyka pamięci natywnej w wersji zapoznawczej programu VS2015](https://devblogs.microsoft.com/cppblog/native-memory-diagnostics-in-vs2015-preview/)  
  
 [Blog C++ wizualny: natywne narzędzia diagnostyczne pamięci dla programu Visual Studio 2015 CTP](https://devblogs.microsoft.com/cppblog/native-memory-diagnostic-tools-for-visual-studio-14-ctp/)
