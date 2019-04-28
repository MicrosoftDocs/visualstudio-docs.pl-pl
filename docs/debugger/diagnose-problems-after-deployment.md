---
title: Diagnozowanie problemów po wdrożeniu | Dokumentacja firmy Microsoft
ms.date: 04/10/2018
ms.topic: conceptual
ms.assetid: a3463eab-a352-4d17-8551-adbaad526db0
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 2adf068fb1e0a668cb6382398601f6aca4743efa
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62897290"
---
# <a name="diagnose-problems-after-deployment-using-intellitrace-c-visual-basic"></a>Diagnozowanie problemów po wdrożeniu za pomocą funkcji IntelliTrace (C#, Visual Basic)

Aby zdiagnozować problemy w aplikacji internetowej ASP.NET po wdrożeniu przy użyciu funkcji IntelliTrace, obejmują informacje o kompilacji za pomocą swojej wersji, aby umożliwić programowi Visual Studio automatycznie znaleźć poprawnych plików źródłowych i plików symboli, które są wymagane do debugowania w dzienniku IntelliTrace.

 Jeśli używasz programu Microsoft Monitoring Agent do kontroli IntelliTrace, należy skonfigurować konfigurowanie monitorowania wydajności aplikacji na serwerze sieci web. Rejestruje zdarzenia diagnostyczne, gdy aplikacja jest uruchamiana i zapisuje zdarzenia w pliku dziennika IntelliTrace. Następnie można przejrzeć zdarzenia w programie Visual Studio Enterprise (ale nie Professional lub Community), przejdź do kodu, w której zaszło zdarzenie, obejrzyj zarejestrowane wartości w danym momencie i przeglądać kod, który uruchomił przodu lub do tyłu. Po znalezieniu i rozwiązać ten problem, powtórz cykl aby stworzyć, opublikować i monitorowania wydania, dzięki czemu można rozwiązać potencjalne problemy w przyszłości wcześniej i szybciej.

 ![Kodu, kompilacji, wersji, monitorowanie, diagnozowanie, poprawianie](../debugger/media/ffr_cycle.png "FFR_Cycle")

 **Będą potrzebne:**

- Visual Studio, DevOps platformy Azure lub serwera Team Foundation Server 2017, 2015, 2013, 2012 lub 2010 do konfigurowania kompilacji

- Program Microsoft Monitoring Agent monitorowania aplikacji i rejestrowanie danych diagnostycznych

- Programu Visual Studio Enterprise (ale nie w wersji Professional lub Community), aby przejrzeć dane diagnostyczne i Debuguj kod przy użyciu funkcji IntelliTrace

## <a name="SetUpBuild"></a> Krok 1: Zawierają informacje o kompilacji za pomocą swojej wersji
 Skonfiguruj proces kompilacji, aby utworzyć manifest kompilacji (*BuildInfo.config* pliku) dla sieci web projektu i obejmują tę manifestu z danej wersji. Ten manifest zawiera informacje dotyczące projektu kontroli źródła i systemu kompilacji, które zostały użyte do utworzenia konkretnej kompilacji. Informacje te pomagają znaleźć pasującego źródła i symboli, po otwarciu dziennika IntelliTrace, aby przejrzeć zarejestrowane zdarzenia z programu Visual Studio.

### <a name="AutomatedBuild"></a> Tworzenie manifestu kompilacji dla zautomatyzowanych kompilacji przy użyciu serwera Team Foundation Server

 Wykonaj następujące kroki, czy używać kontroli wersji serwera Team Foundation lub Git.

#### <a name="TFS2017"></a> Usługa Azure DevOps i Team Foundation Server 2017

Program Visual Studio 2017 i nowsze wersje nie obejmują *BuildInfo.config* pliku, która została zastąpiona, a następnie usuwane. Aby debugować aplikacje sieci web ASP.NET po wdrożeniu, należy użyć jednej z następujących metod:

* W przypadku wdrożenia na platformie Azure, użyj [usługi Application Insights](https://docs.microsoft.com/azure/application-insights/).

* Jeśli musisz używać IntelliTrace, otwórz projekt w programie Visual Studio i ładowanie plików symboli z pasujących kompilacji. Możesz załadować pliki symboli z **modułów** okna lub przez skonfigurowanie symboli w **narzędzia** > **opcje** > **debugowania**   >  **Symbole**.

#### <a name="TFS2013"></a> Team Foundation Server 2013
 Skonfiguruj potok kompilacji, aby dodać lokalizacje źródła, kompilacji i symboli do manifestu kompilacji (BuildInfo.config pliku). Team Foundation Build automatycznie tworzy ten plik i umieszcza go w folderze danych wyjściowych projektu.

1. [Edytuj swój potok kompilacji lub Utwórz nowy potok kompilacji.](/azure/devops/pipelines/get-started-designer?view=vsts)

     ![Wyświetl tworzenie potoku w programie TFS 2013](../debugger/media/ffr_tfs2013viewbuilddefinition.png "FFR_TFS2013ViewBuildDefinition")

2. Wybierz szablon domyślny (TfvcTemplate.12.xaml) lub własny szablon niestandardowy.

     ![Wybierz szablon procesu kompilacji &#45; TFS 2013](../debugger/media/ffr_tfs2013buildprocesstemplate.png "FFR_TFS2013BuildProcessTemplate")

3. Określ miejsce zapisania pliku symboli (PDB), tak, aby Twoje źródło było indeksowane automatycznie.

     Jeśli używasz szablonu niestandardowego, upewnij się, że szablon ma działanie do indeksowania źródła. Należy później dodać argument programu MSBuild, aby określić, gdzie chcesz zapisać pliki symboli.

     ![Ustawianie ścieżki symboli w potoku kompilacji programu TFS 2013](../debugger/media/ffr_tfs2013builddefsymbolspath.png "FFR_TFS2013BuildDefSymbolsPath")

     Aby uzyskać więcej informacji o symbolach, zobacz [opublikować dane symboliczne](/azure/devops/pipelines/tasks/build/index-sources-publish-symbols?view=vsts).

4. Dodaj ten argument MSBuild, aby uwzględnić swoje lokalizacje TFS i symboli w pliku manifestu kompilacji:

     **/p:IncludeServerNameInBuildInfo=True**

     Każdy, kto może uzyskiwać dostęp do serwera sieci web może zobaczyć te lokalizacje w manifeście kompilacji. Upewnij się, że serwer źródłowy jest bezpieczny.

5. Jeśli używasz szablonu niestandardowego, Dodaj ten argument MSBuild, aby określić, gdzie można zapisać pliku symboli:

     **buildsymbolstorepath =**\<*ścieżka do symboli*>

     ![Zawierają informacje o serwerze kompilacji w kompilacji def TFS 2013](../debugger/media/ffr_tfs2013builddefincludeserverinfo.png "FFR_TFS2013BuildDefIncludeServerInfo")

     Dodaj też te linie do pliku projektu sieci Web (.csproj, .vbproj):

    ```xml
    <!-- Import the targets file. Change the folder location as necessary. -->
       <Import Project=""$(MSBuildExtensionsPath)\Microsoft\VisualStudio\v$(VisualStudioVersion)\BuildInfo\Microsoft.VisualStudio.ReleaseManagement.BuildInfo.targets" />

    ```

     Każdy, kto może uzyskiwać dostęp do serwera sieci web może zobaczyć te lokalizacje w manifeście kompilacji. Upewnij się, że serwer źródłowy jest bezpieczny.

6. Uruchom nową kompilację.

    Przejdź do [krok 2: Tworzenie wersji aplikacji](#DeployRelease)

#### <a name="TFS2012_2010"></a> Team Foundation Server 2012 lub 2010
 Wykonaj następujące kroki, aby automatycznie utworzyć manifest kompilacji (plik BuildInfo.config) dla projektu i umieścić ten plik w folderze danych wyjściowych projektu. Plik jest wyświetlany jako "*ProjectName*. BuildInfo.config"w folderze danych wyjściowych, ale jest zmieniona na"BuildInfo.config", w tym folderze wdrożenia po opublikowaniu aplikacji.

1. Na serwerze kompilacji Team Foundation, należy zainstalować program Visual Studio 2013 (w każdej wersji).

2. W potoku kompilacji określ miejsce zapisania symboli tak, aby Twoje źródło było indeksowane automatycznie.

     Jeśli używasz szablonu niestandardowego, upewnij się, że szablon ma działanie do indeksowania źródła.

3. Dodaj następujące argumenty MSBuild do potoku kompilacji:

    - **/p:VisualStudioVersion=12.0**

    - **/p:MSBuildAssemblyVersion=12.0**

    - **/tv:12.0**

    - **/p:IncludeServerNameInBuildInfo=True**

    - **buildsymbolstorepath =**\<*ścieżka do symboli*>

4. Uruchom nową kompilację.

    Przejdź do [krok 2: Tworzenie wersji aplikacji](#DeployRelease)

### <a name="ManualBuild"></a> Tworzenie manifestu kompilacji dla kompilacji ręcznej przy użyciu programu Visual Studio
 Wykonaj następujące kroki, aby automatycznie utworzyć manifest kompilacji (plik BuildInfo.config) dla projektu i umieścić ten plik w folderze danych wyjściowych projektu. Plik jest wyświetlany jako "*ProjectName*. BuildInfo.config"w folderze danych wyjściowych, ale jest zmieniona na"BuildInfo.config", w tym folderze wdrożenia po opublikowaniu aplikacji.

1. W **Eksploratora rozwiązań**, zwolnij projekt sieci web.

2. Otwórz plik projektu (.csproj, .vbproj). Dodaj następujące wiersze:

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

    Przejdź do [krok 2: Tworzenie wersji aplikacji](#DeployRelease)

### <a name="MSBuild"></a> Tworzenie manifestu kompilacji dla kompilacji ręcznej przy użyciu MSBuild.exe
 Dodaj te argumenty kompilacji podczas uruchamiania kompilacji:

 **/p:GenerateBuildInfoConfigFile=True**

 **/p:IncludeServerNameInBuildInfo=True**

 **buildsymbolstorepath =**\<*ścieżka do symboli*>

## <a name="DeployRelease"></a> Krok 2: Tworzenie wersji aplikacji
 Jeśli używasz [pakietu Web.Deploy](https://msdn.microsoft.com/library/dd394698.aspx) utworzony przez proces kompilacji do wdrożenia aplikacji, manifest kompilacji została automatycznie zmieniona z "*ProjectName*. BuildInfo.config"do"BuildInfo.config"i jest umieszczany w tym samym folderze, z pliku Web.config aplikacji na serwerze sieci web.

 Jeśli używasz innych metod do wdrożenia aplikacji, upewnij się, że manifest kompilacji została zmieniona z "*ProjectName*. BuildInfo.config"do"BuildInfo.config"i jest umieszczany w tym samym folderze, z pliku Web.config aplikacji na serwerze sieci web.

## <a name="step-3-monitor-your-app"></a>Krok 3. Monitorowanie aplikacji
 Konfigurowanie monitorowania wydajności aplikacji na serwerze sieci web tak, aby monitorować swoją aplikację w przypadku problemów, rejestrowanie zdarzeń diagnostycznych i zapisać tych zdarzeń do pliku dziennika IntelliTrace. Zobacz [monitorowania wydania dotycząca problemów z wdrażaniem](../debugger/using-the-intellitrace-stand-alone-collector.md).

## <a name="InvestigateEvents"></a> Krok 4: Znajdowanie problemu
 Visual Studio Enterprise należy na komputerze deweloperskim lub innym komputerze, aby przejrzeć zarejestrowane zdarzenia i debugowania kodu za pomocą funkcji IntelliTrace. Można również użyć narzędzi takich jak CodeLens, mapy debugera i mapy kodu, aby pomóc w diagnozowaniu problemu.

### <a name="open-the-intellitrace-log-and-matching-solution"></a>Otwieranie dziennika IntelliTrace i pasującego rozwiązania

1. Otwórz dziennik IntelliTrace (plik .iTrace) z programu Visual Studio Enterprise. Lub po prostu dwukrotnie kliknąć plik, jeśli masz program Visual Studio Enterprise na tym samym komputerze.

2. Wybierz **Otwórz rozwiązanie** z Visual Studio automatycznie otwierał pasujące rozwiązanie lub projekt, jeśli projekt nie został zbudowany jako część rozwiązania. [PYT.: W dzienniku IntelliTrace brakuje informacji o mojej wdrożonej aplikacji. Dlaczego to się stało? Co zrobić?](#InvalidConfigFile)

     Program Visual Studio automatycznie półki oczekujących zmian, po otwarciu pasujące rozwiązanie lub projekt. Aby uzyskać więcej informacji na temat tego zestawu zmian odłożonych, Szukaj w **dane wyjściowe** okna lub **Team Explorer**.

     Przed wprowadzeniem jakichkolwiek zmian, upewnij się, że masz prawidłowe źródło. Jeśli używasz gałęzi, być może pracujesz w innej gałęzi, od których program Visual Studio znajdzie pasujące źródło, takie jak gałąź wydania.

     ![Otwórz rozwiązanie z dziennika IntelliTrace](../debugger/media/ffr_itsummarypageopensolution.png "FFR_ITSummaryPageOpenSolution")

     Jeśli masz istniejący obszar roboczy mapowany do tego rozwiązania lub projektu, Visual Studio wybiera ten obszar roboczy, aby umieścić znalezione źródło.

     ![Otwórz z kontroli źródła do obszaru roboczego mapowanego](../debugger/media/ffr_openprojectfromsourcecontrol_mapped.png "FFR_OpenProjectFromSourceControl_Mapped")

     W przeciwnym wypadku wybierz inny lub utwórz nowy obszar roboczy. Program Visual Studio będzie mapować całą gałąź do tego obszaru roboczego.

     ![Otwórz z kontroli źródła &#45; Utwórz nowy obszar roboczy](../debugger/media/ffr_openprojectfromsourcecontrol_createnewworkspace.png "FFR_OpenProjectFromSourceControl_CreateNewWorkspace")

     Aby utworzyć obszar roboczy z określonymi mapowaniami lub nazwą, która nie jest nazwą komputera, wybierz **Zarządzaj**.

     [PYT.: Dlaczego Visual Studio wskazuje, że moje wybrany obszar roboczy jest nieodpowiedni?](#IneligibleWorkspace)

     [PYT.: Dlaczego nie mogę kontynuować, dopóki nie wybiorę kolekcji zespołu lub innej kolekcji?](#ChooseTeamProject)

### <a name="diagnose-a-performance-problem"></a>Diagnozowanie problemów z wydajnością

1. W obszarze **naruszeń wydajności**, przejrzyj zarejestrowane zdarzenia wydajności, ich całkowity czas realizacji i inne informacje o zdarzeniach. Następnie zagłęb się w metody, które zostały wywołane podczas zdarzenia dotyczącego wydajności.

     ![Wyświetl szczegóły zdarzeń dotyczących wydajności](../debugger/media/ffr_itsummarypageperformance.png "FFR_ITSummaryPagePerformance")

     Możesz także po prostu dwukrotnie kliknąć zdarzenie.

2. Na stronie zdarzeń przejrzyj czasy wykonania dla tych wywołań. Odszukaj spowalniające wywołanie w drzewie wykonywania.

     Najwolniejsze wywołania pojawiają się we własnej sekcji w przypadku wielu wywołań, zagnieżdżonych lub innych.

     Rozwiń to wywołanie, aby przejrzeć wszelkie zagnieżdżone wywołania i wartości, które zostały zarejestrowane w danym momencie. Następnie rozpocznij debugowanie z tego wywołania.

     ![Rozpocznij debugowanie z wywołania metody](../debugger/media/ffr_itsummarypageperformancemethodscalled.png "FFR_ITSummaryPagePerformanceMethodsCalled")

     Można też po prostu dwukrotnie kliknąć wywołanie.

     Jeśli metoda ta jest w kodzie aplikacji, program Visual Studio przechodzi do tej metody.

     ![Przejdź do kodu aplikacji ze zdarzenia wydajności](../debugger/media/ffr_itsummarypageperformancegotocode.png "FFR_ITSummaryPagePerformanceGoToCode")

     Teraz można przejrzeć inne zarejestrowane wartości, stos wywołań, przejść przez kod lub przy użyciu **IntelliTrace** okna [Przenieś tyłu lub do przodu "w czasie" między innymi metodami](../debugger/intellitrace.md) które zostały wywołane podczas tego zdarzenia dotyczącego wydajności.

    - [Co to jest wszystkie te inne zdarzenia i informacje w dzienniku IntelliTrace?](../debugger/using-saved-intellitrace-data.md)
    - [Co jeszcze można zrobić, w tym miejscu?](#WhatElse)
    - [Potrzebujesz więcej informacji na temat zdarzeń dotyczących wydajności?](https://devblogs.microsoft.com/devops/performance-details-in-intellitrace/)

### <a name="diagnose-an-exception"></a>Diagnozowanie wyjątku

1. W obszarze **dane o wyjątkach**, przejrzyj zarejestrowane zdarzenia wyjątków, ich typy, wiadomości, i czas ich wystąpienia. Aby poznać więcej szczegółów związanych z kodem, rozpocznij debugowanie od ostatniego zdarzenia w grupie wyjątków.

     ![Rozpocząć debugowanie ze zdarzenia wyjątków](../debugger/media/ffr_itsummarypageexception.png "FFR_ITSummaryPageException")

     Możesz także po prostu dwukrotnie kliknąć zdarzenie.

     Jeśli wystąpił wyjątek w kodzie aplikacji, program Visual Studio przechodzi do tego miejsca.

     ![Przejdź do kodu aplikacji ze zdarzenia wyjątków](../debugger/media/ffr_itsummarypageexceptiongotocode.png "FFR_ITSummaryPageExceptionGoToCode")

     Teraz można przejrzeć inne zarejestrowane wartości, stos wywołań, lub użyć **IntelliTrace** okna [przenoszenie tyłu lub do przodu "w czasie" między innymi zarejestrowanymi zdarzeniami](../debugger/intellitrace.md), kodu powiązany i wartości odnotowane w te punkty w czasie.

     [Co to jest wszystkie te inne zdarzenia i informacje w dzienniku IntelliTrace?](../debugger/using-saved-intellitrace-data.md)

### <a name="WhatElse"></a> Co jeszcze można zrobić, w tym miejscu?

- [Uzyskaj więcej informacji o tym kodzie](../ide/find-code-changes-and-other-history-with-codelens.md). Aby znaleźć odwołania do tego kodu, historię zmian, powiązane błędy, elementy robocze, przeglądy kodu lub testy jednostkowe, — wszystko bez opuszczania edytora — Użyj wskaźniki CodeLens w edytorze.

     ![Funkcja CodeLens &#45; Wyświetl odwołania do tego kodu](../debugger/media/ffr_itsummarypageperformancecodelensreferences.png "FFR_ITSummaryPagePerformanceCodeLensReferences")

     ![Funkcja CodeLens &#45; Wyświetl historię zmian przez ten kod](../debugger/media/ffr_itsummarypageperformancecodelensauthors.png "FFR_ITSummaryPagePerformanceCodeLensAuthors")

- [Mapuj swoje miejsce w kodzie podczas debugowania.](../debugger/map-methods-on-the-call-stack-while-debugging-in-visual-studio.md) Aby wizualnie śledzić metody, które zostały wywołane podczas sesji debugowania, mapuj stos wywołań.

     ![Mapuj stos wywołań podczas debugowania](../debugger/media/ffr_itsummarypageperformancedebuggermap.png "FFR_ITSummaryPagePerformanceDebuggerMap")

### <a name="FAQ"></a> PYTANIA I ODPOWIEDZI

#### <a name="WhyInclude"></a> Q: Dlaczego zawierają informacje o projekcie, kontroli źródła, kompilacji i symboli z mojego wydania?
 Program Visual Studio używa tych informacji można znaleźć pasujące rozwiązanie i źródła dla wersji, który próbujesz debugować. Po otwarciu dziennika IntelliTrace i wybierz zdarzenie, aby rozpocząć debugowanie, Visual Studio używa symboli do znalezienia i dowiesz się, kod której zaszło zdarzenie. Można przyjrzeć się wartości, które zostały zarejestrowane i szybciej przodu lub do tyłu przez wykonywanie Twojego kodu.

 Jeśli używasz serwera TFS, a informacje te nie znajduje się w manifest kompilacji (BuildInfo.config plik), program Visual Studio szuka zgodnego źródła i symboli na Twoje aktualnie połączone TFS. Jeśli program Visual Studio nie może znaleźć poprawne TFS lub pasujące źródło, zostanie wyświetlony monit wybór różnych TFS.

#### <a name="InvalidConfigFile"></a> Q: W dzienniku IntelliTrace brakuje informacji o mojej wdrożonej aplikacji. Dlaczego to się stało? Co mam zrobić?
 Może się to zdarzyć, gdy wdrażanie z komputera dewelopera lub nie masz połączenia z TFS podczas wdrażania.

1. Przejdź do folderu wdrożenia projektu.

2. Znajdowanie i otwieranie manifest kompilacji (BuildInfo.config plik).

3. Upewnij się, że plik ma wymagane informacje:

- **ProjectName**

   Nazwa projektu w programie Visual Studio. Na przykład:

  ```xml
  <ProjectName>FabrikamFiber.Extranet.Web</ProjectName>
  ```

- **SourceControl**

- Informacje o systemie kontroli źródła i są wymagane właściwości:

  - **TFS**

    - **ProjectCollectionUri**: Identyfikator URI dla kolekcji serwera Team Foundation Server i project

    - **ProjectItemSpec**: Ścieżka do pliku projektu aplikacji (.csproj lub .vbproj)

    - **ProjectVersionSpec**: Wersja projektu

      Na przykład:

    ```xml
    <SourceControl type="TFS">
       <TfsSourceControl>
          <ProjectCollectionUri>http://fabrikamfiber:8080/tfs/FabrikamFiber</ProjectCollectionUri>
          <ProjectItemSpec>$/WorkInProgress/FabrikamFiber/FabrikamFiber.CallCenter/FabrikamFiber.Web/FabrikamFiber.Web.csproj</ProjectItemSpec>
          <ProjectVersionSpec>LFabrikamFiber_BuildAndPublish_20130813@$/WorkInProgress</ProjectVersionSpec>
       </TfsSourceControl>
    </SourceControl>
    ```

  - **Usługa Git**

    - **GitSourceControl**: Lokalizacja **GitSourceControl** schematu

    - **RepositoryUrl**: Identyfikator URI dla serwera Team Foundation Server, kolekcji projektów i repozytorium Git

    - **ProjectPath**: Ścieżka do pliku projektu aplikacji (.csproj lub .vbproj)

    - **CommitId**: Identyfikator dla swojego zatwierdzenia

      Na przykład:

    ```xml
    <SourceControl type="Git">
       <GitSourceControl xmlns="http://schemas.microsoft.com/visualstudio/deploymentevent_git/2013/09">
          <RepositoryUrl>http://gittf:8080/tfs/defaultcollection/_git/FabrikamFiber</RepositoryUrl>
          <ProjectPath>/FabrikamFiber.CallCenter/FabrikamFiber.Web/FabrikamFiber.Web.csproj</ProjectPath>
          <CommitId>50662c96502dddaae5cd5ced962d9f14ec5bc64d</CommitId>
       </GitSourceControl>
    </SourceControl>
    ```

- **Kompilacja**

   Informacje o Twoim systemie kompilacji albo `"TeamBuild"` lub `"MSBuild"`, oraz następujące wymagane właściwości:

  - **BuildLabel** (dla TeamBuild): Nazwa i numer kompilacji. Ta etykieta jest również używane jako nazwa zdarzenia wdrażania. Aby uzyskać więcej informacji na temat numerów kompilacji, zobacz [Użyj kompilacji cyfry jako opisowych nazw zakończonych kompilacji](/azure/devops/pipelines/build/options?view=vsts).

  - **SymbolPath** (zalecane): Lista identyfikatorów URI dla Twojej lokalizacji symboli (plik PDB), rozdzielonych średnikami. Te identyfikatory URI może być adresy URL lub UNC. Ułatwia dla programu Visual Studio można znaleźć pasującego symbole, aby pomóc w debugowaniu.

  - **BuildReportUrl** (dla TeamBuild): Lokalizacja raportu kompilacji w programie TFS

  - **BuildId** (dla TeamBuild): Identyfikator URI dla szczegółów kompilacji w programie TFS. Ten identyfikator URI jest również używane jako identyfikator zdarzenia wdrażania. To musi identyfikator musi być unikatowy, jeśli nie korzystasz z TeamBuild.

  - **BuiltSolution**: Ścieżka do pliku rozwiązania, który korzysta z programu Visual Studio do znajdowania i otwierania pasującego rozwiązania. To jest zawartość **SolutionPath** właściwości programu MsBuild.

    Na przykład:

  - **TFS**

    ```xml
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

    ```xml
    <Build type="MSBuild">
       <MSBuild>
          <SymbolPath>\\gittf\FabrikamFiber.CallCenter\Symbols</SymbolPath>
          <BuiltSolution>/FabrikamFiber.CallCenter/FabrikamFiber.CallCenter.sln</BuiltSolution>
       </MSBuild>
    </Build>
    ```

#### <a name="IneligibleWorkspace"></a> Q: Dlaczego Visual Studio wskazuje, że moje wybrany obszar roboczy jest nieodpowiedni?
 **ODP.:** Wybrany obszar roboczy nie ma żadnych mapowań między folderem kontroli źródła i folderem lokalnym. Aby utworzyć mapowanie dla tego obszaru roboczego, wybierz opcję **Zarządzaj**. W przeciwnym wypadku wybierz już zmapowany obszar roboczy lub utwórz nowy.

 ![Otwórz z kontroli źródła z Brak mapowanego obszaru roboczego](../debugger/media/ffr_openprojectfromsourcecontrol_notmapped.png "FFR_OpenProjectFromSourceControl_NotMapped")

#### <a name="ChooseTeamProject"></a> Q: Dlaczego nie mogę kontynuować, dopóki nie wybiorę kolekcji zespołu lub innej kolekcji?
 **ODP.:** Może się to zdarzyć z następujących powodów:

- Program Visual Studio nie jest połączony z TFS.

     ![Otwórz z kontroli źródła &#45; niepołączony](../debugger/media/ffr_openprojectfromsourcecontrol_notconnected.png "FFR_OpenProjectFromSourceControl_NotConnected")

- Program Visual Studio nie znalazł rozwiązania lub projektu w obecnej kolekcji zespołu.

     Gdy plik manifestu kompilacji (\<*ProjectName*>. BuildInfo.config) nie określa, gdzie program Visual Studio może znaleźć pasujące źródło, Visual Studio używa Twojego obecnie podłączonego TFS, aby znaleźć pasujące rozwiązanie lub projekt. Jeśli Twoja bieżąca kolekcja zespołu nie ma pasującego źródła, program Visual Studio monituje o połączenie z inną kolekcją zespołu.

- Program Visual Studio nie znaleziono rozwiązania lub projektu w kolekcji określonej przez plik manifestu kompilacji (\<*ProjectName*>. BuildInfo.config).

     Określony TFS może już nie mieć pasującego źródła lub może już nawet nie istnieć, być może dlatego, że nastąpiła migracja do nowego TFS. Jeśli określone wystąpienie programu TFS nie istnieje, w programie Visual Studio może upłynąć limit czasu po około minucie, a następnie pojawi się monit o podłączenie do innej kolekcji. Aby kontynuować, należy połączyć się z właściwym serwerem TFS.

     ![Otwórz z kontroli źródła &#45; migracji](../debugger/media/ffr_openprojectfromsourcecontrol_migrated.png "FFR_OpenProjectFromSourceControl_Migrated")

#### <a name="WhatWorkspace"></a> Q: Co to jest obszar roboczy?
 **ODP.:** Twoje [obszar roboczy przechowuje kopię źródła](/azure/devops/repos/tfvc/create-work-workspaces?view=vsts) więc możesz rozwijać i przetestować go oddzielnie przed zaewidencjonowaniem swojej pracy. Jeśli nie masz jeszcze obszaru roboczego, który jest specjalnie zmapowany na znalezione rozwiązania lub projekt, program Visual Studio wyświetli monit, aby wybrać dostępny obszar roboczy lub utworzyć nowy obszar roboczy z nazwą komputera jako domyślną nazwą obszaru roboczego.

#### <a name="UntrustedSymbols"></a> Q: Dlaczego otrzymuję komunikat dotyczący niezaufanych symboli?
 ![Debugowanie przy użyciu ścieżki niezaufanych symboli? ](../debugger/media/ffr_ituntrustedsymbolpaths.png "FFR_ITUntrustedSymbolPaths")

 **ODP.:** Ten komunikat pojawia się, gdy ścieżki symboli w pliku manifestu kompilacji (\<*ProjectName*>. BuildInfo.config) nie jest dołączone do listy zaufanych ścieżek symboli. Możesz dodać ścieżkę do listy ścieżek symboli w opcjach debugera.
