---
title: Konfigurowanie testów jednostkowych za pomocą pliku runsettings
ms.date: 10/03/2019
ms.topic: conceptual
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
author: mikejo5000
ms.openlocfilehash: bd6d2f394edf1a1d2c96404a8af3714fbe9550d6
ms.sourcegitcommit: 5d1b2895d3a249c6bea30eb12b0ad7c0f0862d85
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2020
ms.locfileid: "80880354"
---
# <a name="configure-unit-tests-by-using-a-runsettings-file"></a>Konfigurowanie testów jednostkowych przy użyciu pliku *runsettings*

Testy jednostkowe w programie Visual Studio można skonfigurować przy użyciu pliku *runsettings.* Na przykład można zmienić wersję .NET, na której są uruchamiane testy, katalog wyników testów lub dane, które są zbierane podczas przebiegu testu.

Uruchom pliki ustawień są opcjonalne. Jeśli nie potrzebujesz żadnej specjalnej konfiguracji, nie potrzebujesz pliku *runsettings.* Typowym zastosowaniem pliku *runsettings* jest dostosowanie [analizy pokrycia kodu.](../test/customizing-code-coverage-analysis.md)

## <a name="specify-a-run-settings-file"></a>Określanie pliku ustawień uruchamiania

Uruchom pliki ustawień może służyć do konfigurowania testów, które są uruchamiane z [wiersza polecenia](vstest-console-options.md), w IDE lub w [przepływie pracy kompilacji](/azure/devops/pipelines/test/getting-started-with-continuous-testing?view=vsts) przy użyciu planów testów platformy Azure lub Team Foundation Server (TFS).

### <a name="ide"></a>IDE

::: moniker range="vs-2017"

Aby określić plik ustawień uruchamiania w środowisku IDE, wybierz opcję **Testuj** > **ustawienia** > testu **Wybierz plik ustawień testu,** a następnie wybierz plik *runsettings.*

![Wybieranie menu pliku ustawień testu w programie Visual Studio 2017](media/select-test-settings-file.png)

Plik pojawi się w menu Ustawienia testu i można go zaznaczyć lub usunąć zaznaczenie. Gdy ta opcja jest zaznaczona, plik ustawień uruchamiania jest obowiązuje za każdym razem, gdy wybierzesz **opcję Analizuj pokrycie kodu**.

::: moniker-end

::: moniker range=">=vs-2019"

#### <a name="visual-studio-2019-version-163-and-earlier"></a>Visual Studio 2019 w wersji 16.3 i wcześniejszych

Aby określić plik ustawień uruchamiania w środowisku IDE, wybierz opcję **Testuj** > **wybierz plik ustawień**. Przejdź do pliku *.runsettings* i wybierz go.

![Wybieranie menu pliku ustawień testu w programie Visual Studio 2019](media/vs-2019/select-settings-file.png)

Plik pojawi się w menu Testuj i można go zaznaczyć lub usunąć zaznaczenie. Gdy ta opcja jest zaznaczona, plik ustawień uruchamiania jest obowiązuje za każdym razem, gdy wybierzesz **opcję Analizuj pokrycie kodu**.

#### <a name="visual-studio-2019-version-164-and-later"></a>Visual Studio 2019 w wersji 16.4 i nowszej

Istnieją trzy sposoby określania pliku ustawień uruchamiania w programie Visual Studio 2019 w wersji 16.4 i nowszych:

- Dodaj właściwość kompilacji do projektu za pośrednictwem pliku projektu lub pliku Directory.Build.props. Plik ustawień uruchamiania dla projektu jest określony przez właściwość **RunSettingsFilePath**.

    - Ustawienia przebiegu na poziomie projektu są obecnie obsługiwane w projektach języka C#, VB, C++ i F#.
    - Plik określony dla projektu zastępuje wszystkie inne pliki ustawień uruchamiania określone w rozwiązaniu.
    - [Te właściwości MSBuild](https://docs.microsoft.com/visualstudio/msbuild/msbuild-reserved-and-well-known-properties?view=vs-2019) mogą służyć do określenia ścieżki do pliku runsettings. 

    Przykład określania pliku *runsettings* dla projektu:
    
    ```xml
    <Project Sdk="Microsoft.NET.Sdk">
      <PropertyGroup>
        <RunSettingsFilePath>$(MSBuildProjectDirectory)\example.runsettings</RunSettingsFilePath>
      </PropertyGroup>
      ...
    </Project>
    ```

- Umieść plik ustawień uruchamiania o nazwie ".runsettings" w katalogu głównym rozwiązania.

  Jeśli automatyczne wykrywanie plików ustawień uruchamiania jest włączone, ustawienia w tym pliku są stosowane we wszystkich testach uruchamianych. Można włączyć automatyczne wykrywanie runettings plików z dwóch miejsc:
  
    - **Tools** > **Options** Opcje > narzędzi **Test** > **automatycznego wykrywania runettings plików**

      ![Opcja automatycznego wykrywania pliku runettings w programie Visual Studio 2019](media/vs-2019/auto-detect-runsettings-tools-window.png)
      
    - **Testowanie** > **konfigurowania ustawień uruchamiania** > **Automatyczne wykrywanie plików runettings**
    
      ![Automatyczne wykrywanie pliku runettings w programie Visual Studio 2019](media/vs-2019/auto-detect-runsettings-menu.png)

- W środowisku IDE wybierz opcję **Testuj** > **konfigurowanie ustawień** > **uruchamiania Wybierz plik runsettings o szerokim rozwiązaniu,** a następnie wybierz plik *.runsettings.*

   ![Wybieranie menu pliku runettings dla całego rozwiązania testowego w programie Visual Studio 2019](media/vs-2019/select-solution-settings-file.png)
      
   - Ten plik zastępuje plik ".runsettings" w katalogu głównym rozwiązania, jeśli istnieje i jest stosowany we wszystkich testach uruchamianych.  
   - Ten wybór pliku jest zachowywany tylko lokalnie. 

::: moniker-end

### <a name="command-line"></a>Wiersz polecenia

Aby uruchomić testy z wiersza polecenia, użyj *vstest.console.exe*i określ plik ustawień przy użyciu parametru **/Settings.**

1. Uruchom wiersz polecenia programisty dla programu Visual Studio:

   ::: moniker range="vs-2017"

   W menu **Start** systemu Windows wybierz polecenie Wiersz polecenia dewelopera **programu Visual Studio 2017** > **dla programu VS 2017**.

   ::: moniker-end

   ::: moniker range=">=vs-2019"

   W menu **Start** systemu Windows wybierz polecenie Wiersz polecenia dewelopera **programu Visual Studio 2019** > **dla programu VS 2019**.

   ::: moniker-end

2. Wprowadź polecenie podobne do:

   ```cmd
   vstest.console.exe MyTestAssembly.dll /EnableCodeCoverage /Settings:CodeCoverage.runsettings
   ```

   lub

   ```cmd
   vstest.console.exe --settings:test.runsettings test.dll
   ```

Aby uzyskać więcej informacji, zobacz [opcje wiersza polecenia VSTest.Console.exe](vstest-console-options.md).

## <a name="customize-tests"></a>Dostosowywanie testów

Aby dostosować testy przy użyciu pliku *runsettings,* wykonaj następujące kroki:

1. Dodaj plik XML do rozwiązania programu Visual Studio i zapisz go jako *test.runsettings*.

   > [!TIP]
   > Nazwa pliku nie ma znaczenia, o ile używane jest rozszerzenie *.runsettings*.

2. Zastąp zawartość pliku pliki plikiem XML na podstawie poniższego przykładu i dostosuj ją w razie potrzeby.

::: moniker range="vs-2017"

3. W menu **Test** wybierz polecenie **Wyboru ustawień** > **testu wybierz plik ustawień testu**. Przejdź do utworzonego pliku *runsettings,* a następnie wybierz przycisk **OK**.

::: moniker-end

::: moniker range=">=vs-2019"

3. Aby wybrać plik ustawień uruchamiania, wybierz polecenie **Testuj** > **wybierz plik ustawień**. Przejdź do utworzonego pliku *runsettings,* a następnie wybierz przycisk **OK**.

::: moniker-end

   > [!TIP]
   > W rozwiązaniu można utworzyć więcej niż jeden plik *runsettings* i wybrać go jako aktywny plik ustawień testu, zgodnie z potrzebami.

## <a name="example-runsettings-file"></a>Przykładowy plik *runsettings*

Poniższy kod XML przedstawia zawartość typowego pliku *runsettings.* Każdy element pliku jest opcjonalny, ponieważ ma wartość domyślną.

```xml
<?xml version="1.0" encoding="utf-8"?>
<RunSettings>
  <!-- Configurations that affect the Test Framework -->
  <RunConfiguration>
    <MaxCpuCount>1</MaxCpuCount>
    <!-- Path relative to directory that contains .runsettings file-->
    <ResultsDirectory>.\TestResults</ResultsDirectory>

    <!-- x86 or x64 -->
    <!-- You can also change it from the Test menu; choose "Processor Architecture for AnyCPU Projects" -->
    <TargetPlatform>x86</TargetPlatform>

    <!-- Framework35 | [Framework40] | Framework45 -->
    <TargetFrameworkVersion>Framework40</TargetFrameworkVersion>

    <!-- Path to Test Adapters -->
    <TestAdaptersPaths>%SystemDrive%\Temp\foo;%SystemDrive%\Temp\bar</TestAdaptersPaths>

    <!-- TestSessionTimeout was introduced in Visual Studio 2017 version 15.5 -->
    <!-- Specify timeout in milliseconds. A valid value should be greater than 0 -->
    <TestSessionTimeout>10000</TestSessionTimeout>
  </RunConfiguration>

  <!-- Configurations for data collectors -->
  <DataCollectionRunSettings>
    <DataCollectors>
      <DataCollector friendlyName="Code Coverage" uri="datacollector://Microsoft/CodeCoverage/2.0" assemblyQualifiedName="Microsoft.VisualStudio.Coverage.DynamicCoverageDataCollector, Microsoft.VisualStudio.TraceCollector, Version=11.0.0.0, Culture=neutral, PublicKeyToken=b03f5f7f11d50a3a">
        <Configuration>
          <CodeCoverage>
            <ModulePaths>
              <Exclude>
                <ModulePath>.*CPPUnitTestFramework.*</ModulePath>
              </Exclude>
            </ModulePaths>

            <!-- We recommend you do not change the following values: -->
            <UseVerifiableInstrumentation>True</UseVerifiableInstrumentation>
            <AllowLowIntegrityProcesses>True</AllowLowIntegrityProcesses>
            <CollectFromChildProcesses>True</CollectFromChildProcesses>
            <CollectAspDotNet>False</CollectAspDotNet>

          </CodeCoverage>
        </Configuration>
      </DataCollector>

      <DataCollector uri="datacollector://microsoft/VideoRecorder/1.0" assemblyQualifiedName="Microsoft.VisualStudio.TestTools.DataCollection.VideoRecorder.VideoRecorderDataCollector, Microsoft.VisualStudio.TestTools.DataCollection.VideoRecorder, Version=15.0.0.0, Culture=neutral, PublicKeyToken=b03f5f7f11d50a3a" friendlyName="Screen and Voice Recorder">
        <!--Video data collector was introduced in Visual Studio 2017 version 15.5 -->
        <Configuration>
          <!-- Set "sendRecordedMediaForPassedTestCase" to "false" to add video attachments to failed tests only -->
          <MediaRecorder sendRecordedMediaForPassedTestCase="true"  xmlns="">           
            <ScreenCaptureVideo bitRate="512" frameRate="2" quality="20" />
          </MediaRecorder>
        </Configuration>
      </DataCollector>
    </DataCollectors>
  </DataCollectionRunSettings>

  <!-- Parameters used by tests at run time -->
  <TestRunParameters>
    <Parameter name="webAppUrl" value="http://localhost" />
    <Parameter name="webAppUserName" value="Admin" />
    <Parameter name="webAppPassword" value="Password" />
  </TestRunParameters>

  <!-- Adapter Specific sections -->

  <!-- MSTest adapter -->
  <MSTest>
    <MapInconclusiveToFailed>True</MapInconclusiveToFailed>
    <CaptureTraceOutput>false</CaptureTraceOutput>
    <DeleteDeploymentDirectoryAfterTestRunIsComplete>False</DeleteDeploymentDirectoryAfterTestRunIsComplete>
    <DeploymentEnabled>False</DeploymentEnabled>
    <AssemblyResolution>
      <Directory path="D:\myfolder\bin\" includeSubDirectories="false"/>
    </AssemblyResolution>
  </MSTest>

</RunSettings>
```

## <a name="elements-of-a-runsettings-file"></a>Elementy pliku *runsettings*

Sekcje, które następują szczegółowo elementy pliku *runsettings.*

### <a name="run-configuration"></a>Uruchom konfigurację

```xml
<RunConfiguration>
    <MaxCpuCount>1</MaxCpuCount>
    <ResultsDirectory>.\TestResults</ResultsDirectory>
    <TargetPlatform>x86</TargetPlatform>
    <TargetFrameworkVersion>Framework40</TargetFrameworkVersion>
    <TestAdaptersPaths>%SystemDrive%\Temp\foo;%SystemDrive%\Temp\bar</TestAdaptersPaths>
    <TestSessionTimeout>10000</TestSessionTimeout>
</RunConfiguration>
```

**Element RunConfiguration** może zawierać następujące elementy:

|Węzeł|Domyślne|Wartości|
|-|-|-|
|**WynikiSpektorium**||Katalog, w którym są umieszczane wyniki testów.|
|**Targetframeworkversion**|Framework40|`FrameworkCore10`dla źródeł .NET `FrameworkUap10` Core, dla źródeł opartych na platformie UNIWERSALNEJ systemu `Framework45` `Framework40` IP, dla platformy .NET `Framework35` Framework 4.5 i nowszych, dla platformy .NET Framework 4.0 i .NET Framework 3.5.<br /><br />To ustawienie określa wersję struktury testów jednostkowych używanej do odnajdywanie i wykonywanie testów. Może ona być inna niż wersja platformy .NET określonej we właściwościach kompilacji projektu badania jednostki.<br /><br />Jeśli `TargetFrameworkVersion` element zostanie pominięty z pliku *.runsettings,* platforma automatycznie określa wersję struktury na podstawie wbudowanych plików binarnych.|
|**TargetPlatform (Platformę docelową)**|x86|x86, x64|
|**TreatTestAdapterErrorsAsWarnings**|false|fałsz, prawda|
|**Ścieżki testadapters**||Co najmniej jedna ścieżka do katalogu, w którym znajdują się testadapters|
|**Maksymalna liczbacpu**|1|To ustawienie określa stopień równoległego wykonywania testu podczas uruchamiania testów jednostkowych przy użyciu dostępnych rdzeni na komputerze. Aparat wykonywania testów rozpoczyna się jako odrębny proces na każdym dostępnym rdzeniu i daje każdemu rdzeniu kontener z testami do uruchomienia. Kontener może być zestawem, biblioteką DLL lub odpowiednim artefaktem. Kontener testowy jest jednostką planowania. W każdym kontenerze testy są uruchamiane zgodnie z platformą testową. Jeśli istnieje wiele kontenerów, a następnie po zakończeniu wykonywania testów w kontenerze, są one podane następnego dostępnego kontenera.<br /><br />MaxCpuCount może być:<br /><br />n, gdzie 1 <= n <= liczba rdzeni: do n procesy są uruchamiane<br /><br />n, gdzie n = inna wartość: liczba uruchomionych procesów może wynosić do liczby dostępnych rdzeni. Na przykład ustaw n=0, aby platforma automatycznie decydowania o optymalnej liczbie procesów do uruchomienia w oparciu o środowisko.|
|**TestSessionTimeout (Czas testowania)**||Umożliwia użytkownikom zakończenie sesji testowej, gdy przekroczy ona dany limit czasu. Ustawienie limitu czasu gwarantuje, że zasoby są dobrze zużywane, a sesje testowe są ograniczone do ustawionego czasu. To ustawienie jest dostępne w **programie Visual Studio 2017 w wersji 15.5** i nowszej.|
|**Ścieżka DotnetHostPath**||Określ niestandardową ścieżkę do hosta dotnet, który jest używany do uruchamiania hosta testowego. Jest to przydatne podczas tworzenia własnej dotnet, na przykład podczas tworzenia repozytorium dotnet/runtime. Określenie tej opcji spowoduje pominięcie szukanetesthost.exe i zawsze będzie używać pliku testhost.dll. 

### <a name="diagnostic-data-adapters-data-collectors"></a>Karty danych diagnostycznych (moduły zbierające dane)

**DataCollectors** element określa ustawienia kart danych diagnostycznych. Karty danych diagnostycznych zbierają dodatkowe informacje o środowisku i testowej aplikacji. Każda karta ma ustawienia domyślne i trzeba podać ustawienia tylko wtedy, gdy nie chcesz używać ustawień domyślnych.

#### <a name="code-coverage-adapter"></a>Adapter pokrycia kodu

```xml
<CodeCoverage>
    <ModulePaths>
        <Exclude>
            <ModulePath>.*CPPUnitTestFramework.*</ModulePath>
        </Exclude>
    </ModulePaths>

    <UseVerifiableInstrumentation>True</UseVerifiableInstrumentation>
    <AllowLowIntegrityProcesses>True</AllowLowIntegrityProcesses>
    <CollectFromChildProcesses>True</CollectFromChildProcesses>
    <CollectAspDotNet>False</CollectAspDotNet>
</CodeCoverage>
```

Moduł zbierający dane pokrycia kodu tworzy dziennik z zapisami, które części kodu aplikacji zostały wykonane w teście. Aby uzyskać więcej informacji na temat dostosowywania ustawień pokrycia kodu, zobacz [Dostosowywanie analizy pokrycia kodu](../test/customizing-code-coverage-analysis.md).

#### <a name="video-data-collector"></a>Moduł zbierający dane wideo

Moduł zbierający dane wideo przechwytuje nagrywanie ekranu po uruchomieniu testów. To nagranie jest przydatne do rozwiązywania problemów z testami interfejsu użytkownika. Moduł zbierający dane wideo jest dostępny w **programie Visual Studio 2017 w wersji 15.5** i nowszych.

Aby dostosować inne karty danych diagnostycznych innego typu, użyj [pliku ustawień testu](../test/collect-diagnostic-information-using-test-settings.md).

### <a name="testrunparameters"></a>TestRunParametry

```xml
<TestRunParameters>
    <Parameter name="webAppUrl" value="http://localhost" />
    <Parameter name="docsUrl" value="https://docs.microsoft.com" />
</TestRunParameters>
```

Parametry przebiegu testu umożliwiają definiowanie zmiennych i wartości, które są dostępne dla testów w czasie wykonywania. Dostęp do parametrów przy użyciu <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestContext.Properties%2A?displayProperty=nameWithType> właściwości:

```csharp
[TestMethod]
public void HomePageTest()
{
    string appURL = TestContext.Properties["webAppUrl"];
}
```

Aby użyć parametrów przebiegu <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestContext> testu, <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestContext> dodaj pole prywatne i właściwość publiczną do klasy testowej.

### <a name="mstest-run-settings"></a>Ustawienia uruchamiania MSTest

```xml
<MSTest>
    <MapInconclusiveToFailed>True</MapInconclusiveToFailed>
    <CaptureTraceOutput>false</CaptureTraceOutput>
    <DeleteDeploymentDirectoryAfterTestRunIsComplete>False</DeleteDeploymentDirectoryAfterTestRunIsComplete>
    <DeploymentEnabled>False</DeploymentEnabled>
    <AssemblyResolution>
      <Directory Path="D:\myfolder\bin\" includeSubDirectories="false"/>
    </AssemblyResolution>
</MSTest>
```

Te ustawienia są specyficzne dla karty testowej, <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestMethodAttribute> która uruchamia metody testowe, które mają atrybut.

|Konfigurowanie|Domyślne|Wartości|
|-|-|-|
|**ForcedLegacyMode**|false|W programie Visual Studio 2012 karta MSTest została zoptymalizowana, aby była szybsza i bardziej skalowalna. Niektóre zachowania, na przykład kolejność, w jakiej są uruchamiane testy, mogą nie być dokładnie takie same, jak w poprzednich wersjach programu Visual Studio. Ustaw tę wartość na **true,** aby używać starszej karty testowej.<br /><br />Na przykład można użyć tego ustawienia, jeśli masz plik *app.config* określony dla testu jednostkowego.<br /><br />Zaleca się, aby rozważyć refaktoryzację testów pozwalającą na użycie nowszego adaptera.|
|**IgnoreTestImpact**|false|Funkcja wpływu testu nadaje priorytet testom, na które mają wpływ ostatnie zmiany, po uruchomieniu w programie MSTest lub w programie Microsoft Test Manager (przestarzałym w programie Visual Studio 2017). To ustawienie powoduje wyłączenie funkcji. Aby uzyskać więcej informacji, zobacz [Jakie testy powinny być uruchamiane od poprzedniej kompilacji.](https://msdn.microsoft.com/library/dd286589)|
|**SettingsFile**||W tym miejscu można określić plik ustawień testu, który będzie używany z kartą MSTest. Można również określić plik ustawień testu [z menu ustawień](#ide).<br /><br />Jeśli określisz tę wartość, należy również ustawić **ForcedlegacyMode** **true**.<br /><br />`<ForcedLegacyMode>true</ForcedLegacyMode>`|
|**KeepExecutorAliveAfterLegacyRun**|false|Po zakończeniu przebiegu testu MSTest jest zamykany. Każdy proces, który jest uruchamiany w ramach testu jest również zabity. Jeśli chcesz zachować przy życiu wykonawcę testu, ustaw wartość **true**. Na przykład można użyć tego ustawienia, aby zachować przeglądarkę działającą między kodowanych testów interfejsu użytkownika.|
|**DeploymentEnabled**|true|Jeśli ustawisz wartość **false,** elementy wdrażania określone w metodzie testowej nie są kopiowane do katalogu wdrażania.|
|**CaptureTraceOutput**|true|Można zapisać do śledzenia debugowania z <xref:System.Diagnostics.Trace.WriteLine%2A?displayProperty=nameWithType>metody testowej przy użyciu .|
|**DeleteDeploymentDirectoryAfterTestRunIsComplete**|true|Aby zachować katalog wdrażania po uruchomieniu testu, ustaw tę wartość na **false**.|
|**MapInconclusiveToFailed**|false|Jeśli test zakończy się stanem niejednoznacznym, jest on mapowany na pominięty stan w **Eksploratorze testów.** Jeśli chcesz, aby testy niejednoznaczne były wyświetlane jako nieudane, ustaw wartość **true**.|
|**InProcMode**|false|Jeśli chcesz, aby testy były uruchamiane w tym samym procesie co karta MSTest, ustaw tę wartość na **true**. To ustawienie zapewnia mniejszy przyrost wydajności. Ale jeśli test kończy się z wyjątkiem, pozostałe testy nie są uruchamiane.|
|**Rozwiązanie zgromadzenia**|false|Można określić ścieżki do dodatkowych zestawów podczas znajdowania i uruchamiania testów jednostkowych. Na przykład użyj tych ścieżek dla zestawów zależności, które nie są w tym samym katalogu co zestaw testowy. Aby określić ścieżkę, użyj elementu **Ścieżka katalogowa.** Ścieżki mogą zawierać zmienne środowiskowe.<br /><br />`<AssemblyResolution>  <Directory Path="D:\myfolder\bin\" includeSubDirectories="false"/> </AssemblyResolution>`|

## <a name="see-also"></a>Zobacz też

- [Konfigurowanie przebiegu testowego](https://github.com/microsoft/vstest-docs/blob/master/docs/configure.md)
- [Dostosowywanie analizy pokrycia kodu](../test/customizing-code-coverage-analysis.md)
- [Zadanie testowe programu Visual Studio (plany testów platformy Azure)](/azure/devops/pipelines/tasks/test/vstest?view=vsts)

