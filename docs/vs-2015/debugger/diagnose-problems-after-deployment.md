---
title: Diagnozowanie problemów po wdrożeniu | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: a3463eab-a352-4d17-8551-adbaad526db0
caps.latest.revision: 66
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 41b24cf97ef0768ee700841aa859698cd2307710
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2019
ms.locfileid: "74298300"
---
# <a name="diagnose-problems-after-deployment"></a>Diagnozowanie problemów po wdrożeniu
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Aby zdiagnozować problemy w aplikacji sieci Web ASP.NET po wdrożeniu przy użyciu usługi IntelliTrace, Dołącz informacje o kompilacji do swojej wersji, aby program Visual Studio automatycznie znalazł poprawne pliki źródłowe i pliki symboli wymagane do debugowania dziennika IntelliTrace.  
  
 Jeśli używasz Microsoft Monitoring Agent do kontrolowania IntelliTrace, należy również skonfigurować monitorowanie wydajności aplikacji na serwerze sieci Web. To rejestruje zdarzenia diagnostyczne podczas uruchamiania aplikacji i zapisuje zdarzenia w pliku dziennika IntelliTrace. Możesz przeglądać zdarzenia w Visual Studio Enterprise (ale nie wersje Professional lub Community), przejść do kodu, w którym wystąpiło zdarzenie, przeglądać zarejestrowane wartości w tym momencie i przechodzić do przodu lub do tyłu przez kod, który został uruchomiony. Po znalezieniu i usunięciu problemu Powtórz cykl, aby skompilować, wydać i monitorować swoje wydanie, aby można było rozwiązać przyszłe potencjalne problemy wcześniej i szybciej.  
  
 ![Kod, kompilacja, wydanie, monitorowanie, diagnozowanie, naprawa](../debugger/media/ffr-cycle.png "FFR_Cycle")  
  
 **Będziesz potrzebować:**  
  
- Visual Studio 2015 lub Team Foundation Server 2015, 2013, 2012 lub 2010, aby skonfigurować kompilację  
  
- Microsoft Monitoring Agent monitorowania aplikacji i rejestrowania danych diagnostycznych  
  
- Visual Studio Enterprise (ale nie wersje Professional i Community) do przeglądania danych diagnostycznych i debugowania kodu za pomocą IntelliTrace  
  
## <a name="SetUpBuild"></a>Krok 1. uwzględnianie informacji o kompilacji w wersji  
 Skonfiguruj proces kompilacji, aby utworzyć manifest kompilacji (plik BuildInfo. config) dla projektu sieci Web i dołączyć ten manifest do swojej wersji. Ten manifest zawiera informacje o projekcie, kontroli źródła i systemie kompilacji, które zostały użyte do utworzenia określonej kompilacji. Te informacje ułatwiają programowi Visual Studio znalezienie pasującego źródła i symboli po otwarciu dziennika IntelliTrace w celu przejrzenia zarejestrowanych zdarzeń.  
  
### <a name="AutomatedBuild"></a>Utwórz manifest kompilacji dla zautomatyzowanej kompilacji przy użyciu Team Foundation Server  
 Wykonaj następujące kroki, aby użyć Kontrola wersji serwera Team Foundation lub git.  
  
#### <a name="TFS2013"></a>Team Foundation Server 2013  
 Skonfiguruj definicję kompilacji, aby dodać lokalizacje źródła, kompilacji i symboli do manifestu kompilacji (plik BuildInfo. config). Team Foundation Build automatycznie tworzy ten plik i umieszcza go w folderze wyjściowym projektu.  
  
1. [Edytuj definicję kompilacji lub Utwórz nową definicję kompilacji.](https://msdn.microsoft.com/library/1c2eca2d-9a65-477e-9b23-0678ff7882ee)  
  
    ![Wyświetlanie definicji kompilacji w programie TFS 2013](../debugger/media/ffr-tfs2013viewbuilddefinition.png "FFR_TFS2013ViewBuildDefinition")  
  
2. Wybierz szablon domyślny (TfvcTemplate.12.xaml) lub własny szablon niestandardowy.  
  
    ![Wybieranie szablonu &#45; procesu kompilacji TFS 2013](../debugger/media/ffr-tfs2013buildprocesstemplate.png "FFR_TFS2013BuildProcessTemplate")  
  
3. Określ miejsce zapisania pliku symboli (PDB), aby źródło było indeksowane automatycznie.  
  
    Jeśli używasz szablonu niestandardowego, upewnij się, że szablon ma działanie do indeksowania źródła. Później dodasz argument MSBuild, aby określić, gdzie mają zostać zapisane pliki symboli.  
  
    ![Konfigurowanie ścieżki symboli w definicji kompilacji TFS 2013](../debugger/media/ffr-tfs2013builddefsymbolspath.png "FFR_TFS2013BuildDefSymbolsPath")  
  
    Aby uzyskać więcej informacji na temat symboli, zobacz temat [Publikowanie danych symboli](https://msdn.microsoft.com/library/bd6977ca-e30a-491a-a153-671d81222ce6).  
  
4. Dodaj ten argument MSBuild, aby uwzględnić lokalizacje TFS i symboli w pliku manifestu kompilacji:  
  
    **/p:IncludeServerNameInBuildInfo=True**  
  
    Każdy użytkownik, który ma dostęp do serwera sieci Web, może zobaczyć te lokalizacje w manifeście kompilacji. Upewnij się, że serwer źródłowy jest bezpieczny.  
  
5. Jeśli używasz szablonu niestandardowego, Dodaj ten argument MSBuild, aby określić miejsce zapisania pliku symboli:  
  
    **/p: BuildSymbolStorePath =** \<*ścieżka do symboli*>  
  
    ![Uwzględnij informacje o serwerze kompilacji w kompilacji def TFS 2013](../debugger/media/ffr-tfs2013builddefincludeserverinfo.png "FFR_TFS2013BuildDefIncludeServerInfo")  
  
    Dodaj też te linie do pliku projektu sieci Web (.csproj, .vbproj):  
  
   ```  
   <!-- Import the targets file. Change the folder location as necessary. -->  
      <Import Project=""$(MSBuildExtensionsPath)\Microsoft\VisualStudio\v$(VisualStudioVersion)\BuildInfo\Microsoft.VisualStudio.ReleaseManagement.BuildInfo.targets" />  
  
   ```  
  
6. Uruchom nową kompilację.  
  
   **Krok 2.** [krok 2: wydanie aplikacji](#DeployRelease)  
  
#### <a name="TFS2012_2010"></a>Team Foundation Server 2012 lub 2010  
 Wykonaj następujące kroki, aby automatycznie utworzyć manifest kompilacji (plik BuildInfo. config) dla projektu i umieścić plik w folderze wyjściowym projektu. Plik jest wyświetlany jako "*ProjectName*. BuildInfo. config w folderze wyjściowym, ale zmieniono jego nazwę na "BuildInfo. config" w folderze wdrażania po opublikowaniu aplikacji.  
  
1. Zainstaluj Visual Studio 2013 (dowolna wersja) na serwerze Team Foundation Build.  
  
2. W definicji kompilacji określ miejsce zapisania symboli tak, aby Twoje źródło było indeksowane automatycznie.  
  
    Jeśli używasz szablonu niestandardowego, upewnij się, że szablon ma działanie do indeksowania źródła.  
  
3. Dodaj następujące argumenty MSBuild do swojej definicji kompilacji:  
  
   - **/p:VisualStudioVersion=12.0**  
  
   - **/p: MSBuildAssemblyVersion = 12**  
  
   - **/TV: 12**  
  
   - **/p:IncludeServerNameInBuildInfo=True**  
  
   - **/p: BuildSymbolStorePath =** \<*ścieżka do symboli*>  
  
4. Uruchom nową kompilację.  
  
   **Krok 2.** [krok 2: wydanie aplikacji](#DeployRelease)  
  
### <a name="ManualBuild"></a>Tworzenie manifestu kompilacji dla kompilacji ręcznej przy użyciu programu Visual Studio  
 Wykonaj następujące kroki, aby automatycznie utworzyć manifest kompilacji (plik BuildInfo. config) dla projektu i umieścić plik w folderze wyjściowym projektu. Plik jest wyświetlany jako "*ProjectName*. BuildInfo. config w folderze wyjściowym, ale zmieniono jego nazwę na "BuildInfo. config" w folderze wdrażania po opublikowaniu aplikacji.  
  
1. W **Eksplorator rozwiązań**Zwolnij projekt sieci Web.  
  
2. Otwórz plik projektu (. csproj,. vbproj). Dodaj następujące wiersze:  
  
   ```xml  
   <!-- **************************************************** -->  
   <!-- Build info -->  
   <PropertyGroup>  
      <!-- Generate the BuildInfo.config file -->  
      <GenerateBuildInfoConfigFile>True</GenerateBuildInfoConfigFile>  
      <!-- Include server name in build info -->   
      <IncludeServerNameInBuildInfo>True</IncludeServerNameInBuildInfo>   
      <!-- Include the symbols path so Visual Studio can find the matching deployed code when you start debugging. -->  
      <BuildSymbolStorePath><path to symbols></BuildSymbolStorePath>  
   </PropertyGroup>  
   <!-- **************************************************** -->  
   ```  
  
3. Zaewidencjonuj zaktualizowany plik projektu.  
  
4. Uruchom nową kompilację.  
  
   **Krok 2.** [krok 2: wydanie aplikacji](#DeployRelease)  
  
### <a name="MSBuild"></a>Utwórz manifest kompilacji dla kompilacji ręcznej przy użyciu programu MSBuild. exe  
 Dodaj te argumenty kompilacji podczas uruchamiania kompilacji:  
  
 **/p:GenerateBuildInfoConfigFile=True**  
  
 **/p:IncludeServerNameInBuildInfo=True**  
  
 **/p: BuildSymbolStorePath =** \<*ścieżka do symboli*>  
  
## <a name="DeployRelease"></a>Krok 2. wydawanie aplikacji  
 Jeśli używasz [pakietu Web. deploy](https://msdn.microsoft.com/library/dd394698.aspx) , który został utworzony przez proces kompilacji do wdrożenia aplikacji, zostanie automatycznie zmieniona nazwa manifestu kompilacji z "*ProjectName*". BuildInfo. config "do pliku" BuildInfo. config "i znajduje się w tym samym folderze, w którym znajduje się plik Web. config aplikacji na serwerze sieci Web.  
  
 Jeśli używasz innych metod do wdrożenia aplikacji, upewnij się, że nazwa manifestu kompilacji została zmieniona z "*ProjectName*". BuildInfo. config "do pliku" BuildInfo. config "i znajduje się w tym samym folderze, w którym znajduje się plik Web. config aplikacji na serwerze sieci Web.  
  
## <a name="step-3-monitor-your-app"></a>Krok 3: Monitorowanie aplikacji  
 Skonfiguruj monitorowanie wydajności aplikacji na serwerze sieci Web, aby umożliwić monitorowanie aplikacji pod kątem problemów, rejestrowanie zdarzeń diagnostycznych i zapisywanie tych zdarzeń w pliku dziennika IntelliTrace. Zobacz [monitorowanie wydania pod kątem problemów z wdrażaniem](../debugger/using-the-intellitrace-stand-alone-collector.md).  
  
## <a name="InvestigateEvents"></a>Krok 4. Znajdowanie problemu  
 Musisz Visual Studio Enterprise na komputerze deweloperskim lub innym komputerze, aby przejrzeć zarejestrowane zdarzenia i debugować kod przy użyciu IntelliTrace. Możesz również użyć narzędzi, takich jak CodeLens, mapy debugera i mapy kodu, aby ułatwić zdiagnozowanie problemu.  
  
### <a name="open-the-intellitrace-log-and-matching-solution"></a>Otwieranie dziennika IntelliTrace i pasującego rozwiązania  
  
1. Otwórz dziennik IntelliTrace (plik iTrace) z Visual Studio Enterprise. Lub po prostu kliknij dwukrotnie plik, jeśli masz Visual Studio Enterprise na tym samym komputerze.  
  
2. Wybierz pozycję **Otwórz rozwiązanie** , aby program Visual Studio automatycznie otwierał pasujące rozwiązanie lub projekt, jeśli projekt nie został skompilowany jako część rozwiązania. [P: w dzienniku IntelliTrace brakuje informacji o mojej wdrożonej aplikacji. Dlaczego tak się dzieje? Co mam zrobić?](#InvalidConfigFile)  
  
     Program Visual Studio automatycznie półkuje wszystkie oczekujące zmiany podczas otwierania pasującego rozwiązania lub projektu. Aby uzyskać więcej informacji o tym zestawie odłożonym, zajrzyj do okna **dane wyjściowe** lub **Team Explorer**.  
  
     Przed wprowadzeniem jakichkolwiek zmian upewnij się, że masz prawidłowe źródło. Jeśli używasz rozgałęziania, możesz pracować w innej gałęzi niż w przypadku, gdy program Visual Studio znajdzie pasujące źródło, takie jak gałąź wydania.  
  
     ![Otwórz rozwiązanie z dziennika IntelliTrace](../debugger/media/ffr-itsummarypageopensolution.png "FFR_ITSummaryPageOpenSolution")  
  
     Jeśli masz istniejący obszar roboczy mapowany do tego rozwiązania lub projektu, Visual Studio wybiera ten obszar roboczy, aby umieścić znalezione źródło.  
  
     ![Otwórz z kontroli źródła do zamapowanego obszaru roboczego](../debugger/media/ffr-openprojectfromsourcecontrol-mapped.png "FFR_OpenProjectFromSourceControl_Mapped")  
  
     W przeciwnym wypadku wybierz inny lub utwórz nowy obszar roboczy. Program Visual Studio będzie mapować całą gałąź do tego obszaru roboczego.  
  
     ![Otwórz z kontroli &#45; źródła Utwórz nowy obszar roboczy](../debugger/media/ffr-openprojectfromsourcecontrol-createnewworkspace.png "FFR_OpenProjectFromSourceControl_CreateNewWorkspace")  
  
     Aby utworzyć obszar roboczy z określonymi mapowaniami lub nazwą, która nie jest nazwą komputera, wybierz pozycję **Zarządzaj**.  
  
     [P: Dlaczego program Visual Studio wskazuje, że wybrany obszar roboczy jest nieuprawniony?](#IneligibleWorkspace)  
  
     [P: Dlaczego nie mogę kontynuować, dopóki nie wybiorę kolekcji zespołu lub innej kolekcji?](#ChooseTeamProject)  
  
### <a name="diagnose-a-performance-problem"></a>Diagnozowanie problemów z wydajnością  
  
1. W obszarze **naruszenia wydajności**Sprawdź zarejestrowane zdarzenia wydajności, ich łączny czas wykonywania i inne informacje o zdarzeniach. Następnie zagłęb się w metody, które zostały wywołane podczas zdarzenia dotyczącego wydajności.  
  
     ![Wyświetl szczegóły zdarzenia wydajności](../debugger/media/ffr-itsummarypageperformance.png "FFR_ITSummaryPagePerformance")  
  
     Możesz także po prostu dwukrotnie kliknąć zdarzenie.  
  
2. Na stronie zdarzeń przejrzyj czasy wykonania dla tych wywołań. Odszukaj spowalniające wywołanie w drzewie wykonywania.  
  
     Najwolniejsze wywołania pojawiają się we własnej sekcji w przypadku wielu wywołań, zagnieżdżonych lub innych.  
  
     Rozwiń to wywołanie, aby przejrzeć wszelkie zagnieżdżone wywołania i wartości, które zostały zarejestrowane w danym momencie. Następnie rozpocznij debugowanie z tego wywołania.  
  
     ![Rozpocznij debugowanie od wywołania metody](../debugger/media/ffr-itsummarypageperformancemethodscalled.png "FFR_ITSummaryPagePerformanceMethodsCalled")  
  
     Można też po prostu dwukrotnie kliknąć wywołanie.  
  
     Jeśli metoda ta jest w kodzie aplikacji, program Visual Studio przechodzi do tej metody.  
  
     ![Przejdź do kodu aplikacji ze zdarzenia wydajności](../debugger/media/ffr-itsummarypageperformancegotocode.png "FFR_ITSummaryPagePerformanceGoToCode")  
  
     Teraz można przejrzeć inne zarejestrowane wartości, stos wywołań, przekroczyć kod lub użyć okna **IntelliTrace** do [przenoszenia do tyłu lub do przodu "w czasie" między innymi metodami](../debugger/intellitrace.md) , które zostały wywołane podczas tego zdarzenia wydajności. [Jakie są wszystkie te zdarzenia i informacje w dzienniku IntelliTrace?](../debugger/using-saved-intellitrace-data.md) [Co jeszcze można zrobić w tym miejscu?](#WhatElse) [Potrzebujesz więcej informacji o zdarzeniach dotyczących wydajności?](https://devblogs.microsoft.com/devops/performance-details-in-intellitrace/)  
  
### <a name="diagnose-an-exception"></a>Diagnozowanie wyjątku  
  
1. W obszarze **dane wyjątku**Przejrzyj zarejestrowane zdarzenia wyjątków, ich typy, komunikaty i czas wystąpienia wyjątków. Aby poznać więcej szczegółów związanych z kodem, rozpocznij debugowanie od ostatniego zdarzenia w grupie wyjątków.  
  
     ![Rozpocznij debugowanie od zdarzenia wyjątku](../debugger/media/ffr-itsummarypageexception.png "FFR_ITSummaryPageException")  
  
     Możesz także po prostu dwukrotnie kliknąć zdarzenie.  
  
     Jeśli wystąpił wyjątek w kodzie aplikacji, program Visual Studio przechodzi do tego miejsca.  
  
     ![Przejdź do kodu aplikacji ze zdarzenia wyjątku](../debugger/media/ffr-itsummarypageexceptiongotocode.png "FFR_ITSummaryPageExceptionGoToCode")  
  
     Teraz można przejrzeć inne zarejestrowane wartości, stos wywołań lub użyć okna **IntelliTrace** do [przenoszenia do tyłu lub do przodu "w czasie" między innymi zarejestrowanymi zdarzeniami](../debugger/intellitrace.md), kodem pokrewnym i wartościami zarejestrowanymi w tych punktach w czasie. [Jakie są wszystkie te zdarzenia i informacje w dzienniku IntelliTrace?](../debugger/using-saved-intellitrace-data.md)  
  
### <a name="WhatElse"></a>Co jeszcze można zrobić w tym miejscu?  
  
- [Uzyskaj więcej informacji na temat tego kodu](../ide/find-code-changes-and-other-history-with-codelens.md). Aby znaleźć odwołania do tego kodu, jego historię zmian, powiązane błędy, elementy robocze, przeglądy kodu lub testy jednostkowe — wszystko to bez opuszczania edytora — Użyj wskaźników CodeLens w edytorze.  
  
     ![CodeLens &#45; Wyświetl odwołania do tego kodu](../debugger/media/ffr-itsummarypageperformancecodelensreferences.png "FFR_ITSummaryPagePerformanceCodeLensReferences")  
  
     ![CodeLens &#45; Wyświetl historię zmian dla tego kodu](../debugger/media/ffr-itsummarypageperformancecodelensauthors.png "FFR_ITSummaryPagePerformanceCodeLensAuthors")  
  
- [Mapuj swoje miejsce w kodzie podczas debugowania.](../debugger/map-methods-on-the-call-stack-while-debugging-in-visual-studio.md) Aby wizualnie śledzić metody, które zostały wywołane podczas sesji debugowania, mapuj stos wywołań.  
  
     ![Mapuj stos wywołań podczas debugowania](../debugger/media/ffr-itsummarypageperformancedebuggermap.png "FFR_ITSummaryPagePerformanceDebuggerMap")  
  
### <a name="FAQ"></a> PYTANIA I ODPOWIEDZI  
  
#### <a name="WhyInclude"></a>P: Dlaczego należy uwzględnić informacje o moim projekcie, kontroli źródła, kompilacji i symbolach w mojej wersji?  
 Program Visual Studio używa tych informacji, aby znaleźć pasujące rozwiązanie i źródło dla wersji, którą próbujesz debugować. Po otwarciu dziennika IntelliTrace i wybraniu zdarzenia w celu rozpoczęcia debugowania program Visual Studio używa symboli do znajdowania i wyświetlania kodu, w którym wystąpiło zdarzenie. Następnie można przyjrzeć się wartościom, które zostały zarejestrowane i przenieść do przodu lub do tyłu przez wykonanie kodu.  
  
 Jeśli używasz programu TFS, a te informacje nie są w pliku build manifest (BuildInfo. config), program Visual Studio szuka pasującego źródła i symboli na aktualnie połączonym serwerze TFS. Jeśli program Visual Studio nie może znaleźć poprawnego źródłowego TFS lub pasującego źródła, zostanie wyświetlony monit o wybranie innego TFS.  
  
#### <a name="InvalidConfigFile"></a>P: w dzienniku IntelliTrace brakuje informacji o mojej wdrożonej aplikacji. Dlaczego tak się dzieje? Co mam zrobić?  
 Może się to zdarzyć w przypadku wdrożenia z komputera deweloperskiego lub braku połączenia z programem TFS podczas wdrażania.  
  
1. Przejdź do folderu wdrażania projektu.  
  
2. Znajdź i Otwórz manifest kompilacji (plik BuildInfo. config).  
  
3. Upewnij się, że plik zawiera wymagane informacje:  
  
- **ProjectName**  
  
   Nazwa projektu w programie Visual Studio. Na przykład:  
  
  ```  
  <ProjectName>FabrikamFiber.Extranet.Web</ProjectName>  
  ```  
  
- **SourceControl**  
  
- Informacje o systemie kontroli źródła i wymaganych właściwościach:  
  
  - **TFS**  
  
    - **ProjectCollectionUri**: identyfikator URI dla Team Foundation Server i kolekcji projektów  
  
    - **ProjectItemSpec**: ścieżka do pliku projektu aplikacji (. csproj lub. vbproj)  
  
    - **ProjectVersionSpec**: wersja projektu  
  
      Na przykład:  
  
    ```  
    <SourceControl type="TFS">  
       <TfsSourceControl>  
          <ProjectCollectionUri>http://fabrikamfiber:8080/tfs/FabrikamFiber</ProjectCollectionUri>  
          <ProjectItemSpec>$/WorkInProgress/FabrikamFiber/FabrikamFiber.CallCenter/FabrikamFiber.Web/FabrikamFiber.Web.csproj</ProjectItemSpec>  
          <ProjectVersionSpec>LFabrikamFiber_BuildAndPublish_20130813@$/WorkInProgress</ProjectVersionSpec>  
       </TfsSourceControl>  
    </SourceControl>  
    ```  
  
  - **Usługa Git**  
  
    - **GitSourceControl**: Lokalizacja schematu **GitSourceControl**  
  
    - **RepositoryUrl**: identyfikator URI Team Foundation Server, kolekcji projektów i repozytorium git  
  
    - **ProjectPath**: ścieżka do pliku projektu aplikacji (. csproj lub. vbproj)  
  
    - **CommitId**: Identyfikator zatwierdzenia  
  
      Na przykład:  
  
    ```  
    <SourceControl type="Git">   
       <GitSourceControl xmlns="http://schemas.microsoft.com/visualstudio/deploymentevent_git/2013/09">  
          <RepositoryUrl>http://gittf:8080/tfs/defaultcollection/_git/FabrikamFiber</RepositoryUrl>  
          <ProjectPath>/FabrikamFiber.CallCenter/FabrikamFiber.Web/FabrikamFiber.Web.csproj</ProjectPath>  
          <CommitId>50662c96502dddaae5cd5ced962d9f14ec5bc64d</CommitId>  
       </GitSourceControl>  
    </SourceControl>  
    ```  
  
- {1&gt;Kompilacja&lt;1}  
  
   Informacje o systemie kompilacji, `"TeamBuild"` lub `"MSBuild"`i te wymagane właściwości:  
  
  - **BuildLabel** (dla TeamBuild): Nazwa i numer kompilacji. Ta etykieta jest również używana jako nazwa zdarzenia wdrożenia. Aby uzyskać więcej informacji na temat numerów kompilacji, zobacz [Używanie numerów kompilacji do nadawania znaczących nazw do ukończonych kompilacji](https://msdn.microsoft.com/library/1f302e9d-4b0a-40b5-8009-b69ca6f988c3).  
  
  - **SymbolPath —** (zalecane): Lista identyfikatorów URI dla lokalizacji symboli (pliku PDB) rozdzielonych średnikami. Te identyfikatory URI mogą być adresami URL lub UNCs. Ułatwia to programowi Visual Studio znalezienie pasujących symboli, które ułatwiają debugowanie.  
  
  - **BuildReportUrl** (dla TeamBuild): Lokalizacja raportu kompilacji w programie TFS  
  
  - **BuildID** (dla TeamBuild): identyfikator URI dla szczegółów kompilacji w programie TFS. Ten identyfikator URI jest również używany jako identyfikator zdarzenia wdrożenia. Ta nazwa musi być unikatowa, jeśli nie używasz TeamBuild.  
  
  - **BuiltSolution**: ścieżka do pliku rozwiązania używanego przez program Visual Studio do znajdowania i otwierania pasującego rozwiązania. Jest to zawartość właściwości programu MsBuild **SolutionPath** .  
  
    Na przykład:  
  
  - **TFS**  
  
    ```  
    <Build type="TeamBuild">  
       <MsBuild>  
          <BuildLabel kind="label">FabrikamFiber_BuildAndPublish_20130813.1</BuildLabel>  
          <SymbolPath>\\fabrikamfiber\FabrikamFiber.CallCenter\Symbols</SymbolPath>  
          <BuildReportUrl kind="informative, url" url="http://fabrikamfiber:8080/tfs/FabrikamFiber/_releasePipeline/FindRelease?buildUri=fabrikamfiber%3a%2f%2f%2fBuild%2fBuild%2f448">Build Report Url</BuildReportUrl>  
          <BuildId kind="id">1c4444d2-518d-4673-a590-dce2773c7744,fabrikamfiber:///Build/Build/448</BuildId>  
          <BuiltSolution>$/WorkInProgress/FabrikamFiber/FabrikamFiber.CallCenter/FabrikamFiber.CallCenter.sln</BuiltSolution>  
       </MsBuild>  
    </Build>  
    ```  
  
  - **Usługa Git**  
  
    ```  
    <Build type="MSBuild">   
       <MSBuild>  
          <SymbolPath>\\gittf\FabrikamFiber.CallCenter\Symbols</SymbolPath>  
          <BuiltSolution>/FabrikamFiber.CallCenter/FabrikamFiber.CallCenter.sln</BuiltSolution>  
       </MSBuild>  
    </Build>  
    ```  
  
#### <a name="IneligibleWorkspace"></a>P: Dlaczego program Visual Studio wskazuje, że wybrany obszar roboczy jest nieuprawniony?  
 Odp **.:** Wybrany obszar roboczy nie zawiera żadnych mapowań między folderem kontroli źródła i folderem lokalnym. Aby utworzyć mapowanie dla tego obszaru roboczego, wybierz pozycję **Zarządzaj**. W przeciwnym wypadku wybierz już zmapowany obszar roboczy lub utwórz nowy.  
  
 ![Otwórz z kontroli źródła bez zamapowanego obszaru roboczego](../debugger/media/ffr-openprojectfromsourcecontrol-notmapped.png "FFR_OpenProjectFromSourceControl_NotMapped")  
  
#### <a name="ChooseTeamProject"></a>P: Dlaczego nie mogę kontynuować, dopóki nie wybiorę kolekcji zespołu lub innej kolekcji?  
 Odp **.:** Może się to zdarzyć z jednego z następujących powodów:  
  
- Program Visual Studio nie jest połączony z TFS.  
  
     ![Otwieranie z kontroli &#45; źródła nie jest połączone](../debugger/media/ffr-openprojectfromsourcecontrol-notconnected.png "FFR_OpenProjectFromSourceControl_NotConnected")  
  
- Program Visual Studio nie znalazł rozwiązania lub projektu w obecnej kolekcji zespołu.  
  
     Gdy plik manifestu kompilacji (\<*ProjectName*>. BuildInfo. config) nie określa, gdzie program Visual Studio może znaleźć pasujące źródło, program Visual Studio używa aktualnie połączonego TFS, aby znaleźć pasujące rozwiązanie lub projekt. Jeśli Twoja bieżąca kolekcja zespołu nie ma pasującego źródła, program Visual Studio monituje o połączenie z inną kolekcją zespołu.  
  
- Program Visual Studio nie znalazł rozwiązania lub projektu w kolekcji określonej przez plik manifestu kompilacji (\<*ProjectName*>. BuildInfo. config).  
  
     Określony TFS może już nie mieć pasującego źródła lub może już nawet nie istnieć, być może dlatego, że nastąpiła migracja do nowego TFS. Jeśli określone wystąpienie programu TFS nie istnieje, w programie Visual Studio może upłynąć limit czasu po około minucie, a następnie pojawi się monit o podłączenie do innej kolekcji. Aby kontynuować, należy połączyć się z właściwym serwerem TFS.  
  
     ![Otwórz z migrowanej &#45; kontroli źródła](../debugger/media/ffr-openprojectfromsourcecontrol-migrated.png "FFR_OpenProjectFromSourceControl_Migrated")  
  
#### <a name="WhatWorkspace"></a>P: co to jest obszar roboczy?  
 Odp **.:** [Obszar roboczy przechowuje kopię źródła](https://msdn.microsoft.com/library/1d7f6ed8-ec7c-48f8-86da-9aea55a90d5a) , dzięki czemu można go opracowywać i testować oddzielnie przed zaewidencjonowaniem pracy. Jeśli nie masz jeszcze obszaru roboczego, który jest specjalnie zmapowany na znalezione rozwiązania lub projekt, program Visual Studio wyświetli monit, aby wybrać dostępny obszar roboczy lub utworzyć nowy obszar roboczy z nazwą komputera jako domyślną nazwą obszaru roboczego.  
  
#### <a name="UntrustedSymbols"></a>P: Dlaczego otrzymuję komunikat dotyczący niezaufanych symboli?  
 ![Debuguj przy użyciu ścieżki niezaufanych symboli?](../debugger/media/ffr-ituntrustedsymbolpaths.png "FFR_ITUntrustedSymbolPaths")  
  
 Odp **.:** Ten komunikat pojawia się, gdy ścieżka symboli w pliku manifestu kompilacji (\<*ProjectName*>. BuildInfo. config) nie znajduje się na liście ścieżek symboli zaufanych. Możesz dodać ścieżkę do listy ścieżek symboli w opcjach debugera.
