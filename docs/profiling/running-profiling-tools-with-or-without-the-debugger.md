---
title: Uruchamianie narzędzi z lub bez debugera profilowania | Dokumentacja firmy Microsoft
ms.date: 11/04/2018
ms.topic: conceptual
ms.assetid: 3fcdccad-c1bd-4c67-bcec-bf33a8fb5d63
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: a6f7b61bc3dd6f11bf16808df15d9c2dad1222f6
ms.sourcegitcommit: 752f03977f45169585e407ef719450dbe219b7fc
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/15/2019
ms.locfileid: "56316915"
---
# <a name="run-profiling-tools-with-or-without-the-debugger"></a>Uruchamianie narzędzi profilowania z debugerem lub bez debugera

Visual Studio oferuje szeroki wybór pomiaru wydajności i narzędzia profilowania. Niektóre narzędzia, takie jak **użycie procesora CPU** i **użycie pamięci**, można uruchomić z lub bez debugera i w wersji lub konfiguracji kompilacji debugowania. **Profiler wydajności** narzędzi, takich jak **oś czasu aplikacji** można uruchamiać na debugowanie lub wydanie kompilacji. Zintegrowane z debugerem narzędzi, takich jak **narzędzia diagnostyczne** okna i **zdarzenia** kartę działania tylko podczas sesji debugowania.  

>[!NOTE]
>Można użyć narzędzi wydajności bez debugera, system Windows 7 lub nowszy. Windows 8 lub nowszy jest wymagany do uruchomienia narzędzia profilowania zintegrowane z debugerem.

Bez debugera **Profiler wydajności** i zintegrowane z debugerem **narzędzia diagnostyczne** podać inne informacje i środowisk. Narzędzia zintegrowane z debugerem Pokaż punkty przerwania i wartości zmiennych. Narzędzi bez debugera mu wyniki bliżej użytkownika końcowego. 

Aby zdecydować, które narzędzia i wyników do użycia, należy wziąć pod uwagę następujące kwestie:

- Problemy z wydajnością zewnętrznych, takich jak We/Wy pliku lub problemów z czasem odpowiedzi sieci, nie będą różnić się znacznie w narzędziach debuger lub bez debugera. 
- Problemy spowodowane przez wywołania mocy procesora CPU może być wydajności znaczne różnice między wersjami Zwolnij i Debuguj. Sprawdź, czy problem występuje w wersji kompilacji. 
- Jeśli ten problem występuje tylko w kompilacjach debugowania, prawdopodobnie nie trzeba uruchamiać narzędzia bez debugera. W wersji można tworzyć problemy, zdecyduj, czy narzędzia debuger może pomóc w celu bliższego zbadania problemu. 
- Kompilacje wydania Podaj jak wbudowanie wywołania funkcji i stałe, czyszczenia ścieżek kodu nieużywanych i przechowywanie zmienne w sposób, który nie może być używany przez debuger. Numery wydajność w narzędziach zintegrowane z debugerem są mniej dokładne, ponieważ kompilacje debugowania braku tych optymalizacjach. 
- Sam debuger zmienia czas wydajności, jak debugera niezbędne operacje, takie jak przechwytuje wyjątek i zdarzenia ładowania modułu. 
- Wydajność numery kompilacji do wydania **Profiler wydajności** narzędzia są dokładne i dokładne. Wyniki działania narzędzia zintegrowane z debugerem są najbardziej przydatne do porównania z innych pomiarów związanym z debugowaniem.

##  <a name="BKMK_Quick_start__Collect_diagnostic_data"></a> Zbieranie danych profilowania podczas debugowania  

Po rozpoczęciu debugowania w programie Visual Studio, wybierając **debugowania** > **Rozpocznij debugowanie** lub naciskając **F5**, **narzędzia diagnostyczne** domyślnie zostanie wyświetlone okno. Aby otworzyć go ręcznie, zaznacz **debugowania** > **Windows** > **Pokaż narzędzia diagnostyczne**. **Narzędzia diagnostyczne** okno zawiera informacje dotyczące zdarzenia, pamięć procesu i użycie procesora CPU.  

![Narzędzia diagnostyczne](../profiling/media/diagnostictools-update1.png "narzędzia diagnostyczne")  

- Użyj **ustawienia** ikonę na pasku narzędzi, aby wybrać, czy chcesz wyświetlić **użycie pamięci**, **analiza interfejsu użytkownika**, i **użycie procesora CPU**. 
  
- Wybierz **ustawienia** w **ustawienia** listę rozwijaną, aby otworzyć **diagnostycznych strony właściwości narzędzia** więcej opcji. 
  
- Jeśli korzystasz z programu Visual Studio Enterprise, można włączyć lub wyłączyć funkcji IntelliTrace w programie Visual Studio **narzędzia** > **opcje** > **IntelliTrace**.  
  
Sesja diagnostyczna kończy się po zatrzymaniu debugowania.  
  
Można również wyświetlić **narzędzia diagnostyczne** dla zdalnego debugowania elementów docelowych. Dla zdalnego debugowania i profilowania zdalny debuger programu Visual Studio musi być zainstalowana i uruchomiona w zdalnym elemencie docelowym. 
- Zdalne debugowanie i profilowanie aplikacji klasycznej projektów, zobacz [zdalne debugowanie](../debugger/remote-debugging.md). 
- Zdalne debugowanie i profilowanie aplikacji platformy uniwersalnej systemu Windows, zobacz [debugowanie aplikacji platformy UWP na komputerach zdalnych](../debugger/run-windows-store-apps-on-a-remote-machine.md). 

### <a name="the-events-tab"></a>Na karcie zdarzenia

Podczas sesji debugowania **zdarzenia** karcie **narzędzia diagnostyczne** okna Wyświetla zdarzenia diagnostyczne, które wystąpiły. Prefiksy kategorii: **Punkt przerwania**, **pliku**, i inne, pozwalają na szybkie skanowanie listy kategorii lub pominąć kategorii nie dba o.  
  
Użyj **filtru** listę rozwijaną, aby filtrowanie zdarzeń i widok przez zaznaczenie lub usunięcie zaznaczenia tej opcji określonych kategorii zdarzenia. 

![Filtr zdarzeń diagnostycznych](../profiling/media/diagnosticeventfilter.png "filtr zdarzeń diagnostycznych")  

Użyj pola wyszukiwania, aby znaleźć określony ciąg na liście zdarzeń. Poniżej przedstawiono wyniki wyszukiwania dla ciągu "name", który jest zgodny z czterech zdarzenia:  

![Wyszukiwanie zdarzeń diagnostycznych](../profiling/media/diagnosticseventsearch.png "wyszukiwanie zdarzeń diagnostycznych")  

Aby uzyskać więcej informacji, zobacz [wyszukiwanie i filtrowanie na karcie zdarzenia w oknie narzędzia diagnostyczne](https://devblogs.microsoft.com/devops/searching-and-filtering-the-events-tab-of-the-diagnostic-tools-window/).  

## <a name="collect-profiling-data-without-debugging"></a>Zbieranie danych profilowania bez debugowania  

Aby zbierać dane dotyczące wydajności bez debugowania, możesz uruchomić **Profiler wydajności** narzędzia. Niektóre z narzędzi profilowania wymagają uprawnień administratora do uruchomienia. Możesz uruchomić program Visual Studio jako administrator lub narzędzia można uruchomić jako administrator, podczas uruchamiania sesji diagnostycznej.  
   
1. Otwarty projekt w programie Visual Studio, wybierz **debugowania** > **Profiler wydajności**, lub naciśnij **Alt**+**F2**.  
   
1. Na stronie diagnostyki uruchamiania wybierz co najmniej jedno narzędzie do uruchomienia. Wyświetlane są tylko narzędzia, które mają zastosowanie do typu projektu, systemu operacyjnego i język programowania. Wybierz **Pokaż wszystkie narzędzia** się również narzędzia, które są wyłączone dla tej sesji diagnostycznej. Poniżej przedstawiono wybrane opcje może wyglądać dla aplikacji platformy uniwersalnej systemu Windows C#:  
   
   ![Wybierz narzędzia diagnostyczne](../profiling/media/diag_selecttool.png "DIAG_SelectTool")  
   
1. Aby uruchomić sesji diagnostycznej, zaznacz **Start**.  
   
   Gdy sesja jest uruchomiona, niektóre narzędzia wyświetlana wykresów danych w czasie rzeczywistym na stronie narzędzia diagnostyczne.  
   
    ![Zbieranie danych w Centrum wydajności i diagnostyki](../profiling/media/pdhub_collectdata.png "centrum zbierania danych")  
   
1. Aby zakończyć sesji diagnostycznej, wybierz **Zatrzymaj Kolekcjonowanie**.  
   
   Przeanalizowany dane są wyświetlane na **raportu** strony.  
  
Można zapisywać raporty i otworzyć je z **ostatnio otwierane sesje** listy na stronie uruchamiania narzędzia diagnostyczne.  

![Otwórz plik sesji diagnostyki zapisane](../profiling/media/pdhub_openexistingdiagsession.png "PDHUB_OpenExistingDiagSession")  
  
### <a name="the-profiling-report"></a>Raport profilowania  
 ![Raport narzędzia diagnostyczne](../profiling/media/diag_report.png "DIAG_Report")  
  
|||  
|-|-|  
|![Krok 1](../profiling/media/procguid_1.png "ProcGuid_1")|Na osi czasu są widoczne długość sesji profilowania, zdarzenia aktywacji cyklu życia aplikacji i znaczniki użytkownika.|  
|![Krok 2](../profiling/media/procguid_2.png "ProcGuid_2")|Raport można ograniczyć do części osi czasu, przeciągając niebieskie paski w celu wybrania regionu na osi czasu.|  
|![Krok 3](../profiling/media/procguid_3.png "ProcGuid_3")|Każde narzędzie diagnostyczne wyświetla co najmniej jeden główny wykresów. Jeśli Twoja sesja diagnostyczna więcej niż jednego narzędzia, zostaną wyświetlone wszystkie ich wzorca wykresów.|  
|![Krok 4](../profiling/media/procguid_4.png "ProcGuid_4")|Można zwijać i rozwijać poszczególnych wykresów każdego z tych narzędzi.|  
|![Krok 5](../profiling/media/procguid_6.png "ProcGuid_6")|Gdy dane zawiera więcej niż jednego narzędzia, narzędzie szczegółowe informacje są zbierane na kartach.|  
|![Krok 6](../profiling/media/procguid_6a.png "ProcGuid_6a")|Dolnej części raportu zawiera jeden lub więcej widoków szczegółów dla każdego narzędzia. Widok można filtrować, wybierając regionów na osi czasu.|  
  
## <a name="run-diagnostic-sessions-on-installed-or-running-apps"></a>Uruchamianie sesji diagnostyki na zainstalowanych i uruchomionych aplikacji 

 Oprócz uruchamianie aplikacji z projektu programu Visual Studio, można również uruchomić sesje diagnostyki na alternatywnych obiektów docelowych. Na przykład możesz chcieć diagnozować problemy z wydajnością w aplikacji, która została zainstalowana z Windows Store App.  
  
 ![Wybierz cel analizy narzędzia diagnostyczne](../profiling/media/pdhub_chooseanalysistarget.png "PDHUB_ChooseAnalysisTarget")  
  
 Można uruchomić aplikacji, które są już zainstalowane lub Dołącz narzędzia diagnostyczne do aplikacji i procesów, które zostały już uruchomione. Po wybraniu **uruchamiania aplikacji** lub **zainstalowana aplikacja**, wybierz aplikację z listy, która umożliwia znalezienie aplikacji na docelowy określonego wdrożenia. Ten element docelowy może być na komputerze lokalnym lub zdalnym. 
  
 ![Wybór uruchomionej lub zainstalowanych aplikacji diagnostyki](../profiling/media/pdhub_selectrunningapp.png "PDHUB_SelectRunningApp")  
  
## <a name="see-also"></a>Zobacz także

Poniżej przedstawiono, blogi i artykuły w witrynie MSDN z zespołu programistycznego diagnostyki:  
 [Magazyn MSDN: Analizowanie wydajności podczas debugowania w programie Visual Studio 2015](https://msdn.microsoft.com/magazine/dn973013.aspx)
  
 [Magazyn MSDN: Użyj funkcji IntelliTrace, aby szybciej diagnozować problemy](https://msdn.microsoft.com/magazine/dn973014.aspx)
  
 [Wpis w blogu: Diagnozowanie przecieków procedury obsługi zdarzeń za pomocą narzędzia użycie pamięci w programie Visual Studio 2015](https://devblogs.microsoft.com/devops/diagnosing-event-handler-leaks-with-the-memory-usage-tool-in-visual-studio-2015/)
  
 [Wideo: Debugowanie historyczne za pomocą IntelliTrace w programie Microsoft Visual Studio Ultimate 2015](https://channel9.msdn.com/Events/Ignite/2015/BRK3716)
  
 [Wideo: Debugowanie problemów z wydajnością za pomocą programu Visual Studio 2015](https://channel9.msdn.com/Events/Build/2015/3-731)
  
 [Perftip: Wydajność informacji o skrócie podczas debugowania przy użyciu programu Visual Studio](https://devblogs.microsoft.com/devops/perftips-performance-information-at-a-glance-while-debugging-with-visual-studio/)
  
 [Okno debugera narzędzia diagnostyczne w programie Visual Studio 2015](https://devblogs.microsoft.com/devops/diagnostic-tools-debugger-window-in-visual-studio-2015/)
  
 [Funkcja IntelliTrace w Visual Studio Enterprise 2015](https://devblogs.microsoft.com/devops/intellitrace-in-visual-studio-ultimate-2015/)
