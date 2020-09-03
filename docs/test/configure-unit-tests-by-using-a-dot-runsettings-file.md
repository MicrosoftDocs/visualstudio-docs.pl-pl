---
title: Konfigurowanie testów jednostkowych przy użyciu pliku. runsettings
ms.date: 07/15/2020
ms.topic: conceptual
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
author: mikejo5000
ms.openlocfilehash: f638d60b7bd4416bb7a19cc960cac1159c755ab3
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "86972299"
---
# <a name="configure-unit-tests-by-using-a-runsettings-file"></a>Konfigurowanie testów jednostkowych przy użyciu pliku *. runsettings*

Testy jednostkowe w programie Visual Studio można skonfigurować przy użyciu pliku *. runsettings* . Na przykład można zmienić wersję platformy .NET, w której testy są uruchamiane, katalog dla wyników testu lub dane, które są zbierane podczas przebiegu testowego. Typowym zastosowaniem pliku *. runsettings* jest dostosowanie [analizy pokrycia kodu](../test/customizing-code-coverage-analysis.md).

Pliki parametrów uruchomieniowych mogą służyć do konfigurowania testów uruchamianych z [wiersza polecenia](vstest-console-options.md), z IDE lub w [przepływie pracy kompilacji](/azure/devops/pipelines/test/getting-started-with-continuous-testing?view=vsts) przy użyciu Azure test PLANS lub Team Foundation Server (TFS).

Pliki parametrów uruchomieniowych są opcjonalne. Jeśli nie jest wymagana żadna specjalna konfiguracja, nie jest potrzebny plik *. runsettings* .

## <a name="create-a-run-settings-file-and-customize-it"></a>Utwórz plik parametrów uruchomieniowych i dostosuj go

1. Dodaj plik parametrów uruchomieniowych do rozwiązania. W **Eksplorator rozwiązań**w menu skrótów rozwiązania wybierz pozycję **Dodaj**  >  **nowy element**i wybierz pozycję **plik XML**. Zapisz plik z nazwą, taką jak *test. runsettings*.

   > [!TIP]
   > Nazwa pliku nie ma znaczenia, o ile używasz rozszerzenia *runsettings*.

2. Dodaj zawartość z [przykładu *. runsettings](#example-runsettings-file), a następnie dostosuj ją do swoich potrzeb zgodnie z opisem w poniższych sekcjach.

3. Określ plik *. runsettings, którego chcesz użyć, używając jednej z następujących metod:

   - [Visual Studio IDE](#specify-a-run-settings-file-in-the-ide)
   - [Wiersz polecenia](#specify-a-run-settings-file-from-the-command-line)
   - [Kompilowanie przepływu pracy](/azure/devops/pipelines/test/getting-started-with-continuous-testing?view=vsts) przy użyciu Azure Test Plans lub Team Foundation Server (TFS).

4. Uruchom testy jednostkowe, aby użyć niestandardowych ustawień uruchomieniowych.

::: moniker range="vs-2017"

Jeśli chcesz wyłączyć ustawienia niestandardowe i włączyć je w IDE, usuń zaznaczenie lub wybierz plik z **Test** > menu **Ustawienia testu** testowego.

![Menu ustawień testu z niestandardowym plikiem ustawień w programie Visual Studio 2017](../test/media/codecoverage-settingsfile.png)

::: moniker-end

::: moniker range=">=vs-2019"

Jeśli chcesz wyłączyć ustawienia niestandardowe i włączyć je w IDE, usuń zaznaczenie lub wybierz plik w menu **test** .

::: moniker-end

> [!TIP]
> W rozwiązaniu można utworzyć więcej niż jeden plik *. runsettings* i wybrać jeden z nich jako aktywny plik ustawień testu.

## <a name="specify-a-run-settings-file-in-the-ide"></a>Określ plik parametrów uruchomieniowych w środowisku IDE

Dostępne metody zależą od używanej wersji programu Visual Studio.

::: moniker range="vs-2017"
Aby określić plik parametrów uruchomieniowych w środowisku IDE **, wybierz pozycję Testuj** > **Ustawienia testu** > **Wybierz plik ustawień testu**, a następnie wybierz plik *. runsettings* .

![Wybieranie menu plik ustawień testu w programie Visual Studio 2017](media/select-test-settings-file.png)

Plik jest wyświetlany w menu Ustawienia testu i można go zaznaczyć lub usunąć jego zaznaczenie. Gdy jest zaznaczone, plik parametrów uruchomieniowych ma zastosowanie zawsze, gdy wybierzesz opcję **Analizuj pokrycie kodu**.
::: moniker-end

::: moniker range=">=vs-2019"

### <a name="visual-studio-2019-version-164-and-later"></a>Visual Studio 2019 w wersji 16,4 lub nowszej

Istnieją trzy sposoby określania pliku parametrów uruchomieniowych w programie Visual Studio 2019 w wersji 16,4 lub nowszej.

- [Automatycznie Wykryj Parametry uruchomieniowe](#autodetect-the-run-settings-file)
- [Ręcznie ustaw Parametry uruchomieniowe](#manually-select-the-run-settings-file)
- [Ustawianie właściwości kompilacji](#set-a-build-property)

#### <a name="autodetect-the-run-settings-file"></a>Automatycznie wykrywaj plik parametrów uruchomieniowych

Aby automatycznie wykryć plik parametrów uruchomieniowych, umieść go w katalogu głównym rozwiązania.

Jeśli jest włączone Autowykrywanie plików uruchomieniowych, ustawienia w tym pliku są stosowane do wszystkich przebiegów testów. Funkcję automatycznego wykrywania plików runsettings można włączyć przy użyciu dwóch metod:
  
- Wybierz **Tools** > **Opcje** narzędzi > **test** > **autowykrywania runsettings plików**

   ![Automatycznie Wykryj opcję pliku runsettings w programie Visual Studio 2019](media/vs-2019/auto-detect-runsettings-tools-window.png)
      
- Wybierz kolejno pozycje **Testuj** > **Skonfiguruj Parametry uruchomieniowe** > **Autowykrywanie plików runsettings**
    
   ![Autowykrywanie menu plik runsettings w programie Visual Studio 2019](media/vs-2019/auto-detect-runsettings-menu.png)

#### <a name="manually-select-the-run-settings-file"></a>Ręcznie wybierz plik parametrów uruchomieniowych

W środowisku IDE wybierz kolejno opcje **Testuj** > **Skonfiguruj Parametry uruchomieniowe** > **Wybierz pozycję plik Wide runsettings**, a następnie wybierz plik *. runsettings* .

   - Ten plik przesłania plik *. runsettings* w katalogu głównym rozwiązania, jeśli istnieje, i jest stosowany do wszystkich przebiegów testów.  
   - Ten wybór pliku będzie trwały tylko lokalnie.

![Wybieranie rozwiązania testowego — menu plik runsettings w programie Visual Studio 2019](media/vs-2019/select-solution-settings-file.png)

#### <a name="set-a-build-property"></a>Ustawianie właściwości kompilacji

Dodaj właściwość Build do projektu za pomocą pliku projektu lub pliku Directory. Build. props. Plik parametrów uruchomieniowych dla projektu jest określany przez właściwość **RunSettingsFilePath**.

- Ustawienia uruchomieniowe na poziomie projektu są obecnie obsługiwane w projektach C#, VB, C++ i F #.
- Plik określony dla projektu zastępuje wszystkie inne pliki parametrów uruchomieniowych określone w rozwiązaniu.
- [Te właściwości programu MSBuild](https://docs.microsoft.com/visualstudio/msbuild/msbuild-reserved-and-well-known-properties?view=vs-2019) mogą służyć do określania ścieżki do pliku runsettings. 

Przykład określenia pliku *. runsettings* dla projektu:
    
```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <RunSettingsFilePath>$(MSBuildProjectDirectory)\example.runsettings</RunSettingsFilePath>
  </PropertyGroup>
  ...
</Project>
```

### <a name="visual-studio-2019-version-163-and-earlier"></a>Visual Studio 2019 w wersji 16,3 i starszej

Aby określić plik parametrów uruchomieniowych w IDE, wybierz pozycję **Testuj**  >  **Wybierz plik ustawień**. Przejdź do pliku *. runsettings* i wybierz go.

![Wybieranie menu plik ustawień testu w programie Visual Studio 2019](media/vs-2019/select-settings-file.png)

Plik jest wyświetlany w menu test i można go zaznaczyć lub usunąć jego zaznaczenie. Gdy jest zaznaczone, plik parametrów uruchomieniowych ma zastosowanie zawsze, gdy wybierzesz opcję **Analizuj pokrycie kodu**.
::: moniker-end

## <a name="specify-a-run-settings-file-from-the-command-line"></a>Określ plik parametrów uruchomieniowych z wiersza polecenia

Aby uruchomić testy z wiersza polecenia, użyj *vstest.console.exe*i określ plik ustawień przy użyciu parametru **/Settings** .

1. Otwórz [wiersz polecenia dla deweloperów](/dotnet/framework/tools/developer-command-prompt-for-vs) dla programu Visual Studio.

2. Wprowadź polecenie podobne do:

   ```cmd
   vstest.console.exe MyTestAssembly.dll /EnableCodeCoverage /Settings:CodeCoverage.runsettings
   ```

   lub

   ```cmd
   vstest.console.exe --settings:test.runsettings test.dll
   ```

Aby uzyskać więcej informacji, zobacz [VSTest.Console.exe opcje wiersza polecenia](vstest-console-options.md).

## <a name="the-runsettings-file"></a>Plik *. runsettings

Plik *. runsettings jest plikiem XML, który zawiera różne elementy konfiguracji w obrębie elementu **runsettings** . Poniższe sekcje zawierają szczegółowe informacje o różnych elementach. Pełny przykład można znaleźć w [pliku example *. runsettings](#example-runsettings-file).

```xml
<?xml version="1.0" encoding="utf-8"?>
<RunSettings>
  <!-- configuration elements -->
</RunSettings>
```

Każdy element konfiguracji jest opcjonalny, ponieważ ma wartość domyślną.

## <a name="runconfiguration-element"></a>RunConfiguration, element

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

Element **RunConfiguration** może zawierać następujące elementy:

|Węzeł|Domyślne|Wartości|
|-|-|-|
|**MaxCpuCount**|1|To ustawienie określa stopień równoległego wykonywania testów podczas uruchamiania testów jednostkowych przy użyciu dostępnych rdzeni na komputerze. Aparat wykonywania testu jest uruchamiany jako proces odrębny dla każdego dostępnego rdzenia i zapewnia każdy rdzeń kontenera z testami do uruchomienia. Kontener może być zestawem, biblioteką DLL lub odpowiednim artefaktem. Kontener testowy jest jednostką planowania. W każdym kontenerze testy są uruchamiane zgodnie z platformą testową. Jeśli istnieje wiele kontenerów, a następnie procesy ukończyą wykonywanie testów w kontenerze, otrzymają następny dostępny kontener.<br /><br />MaxCpuCount może:<br /><br />n, gdzie 1 <= n <= liczba rdzeni: uruchomiono do n procesów<br /><br />n, gdzie n = jakakolwiek inna wartość: liczba uruchomionych procesów może być równa liczbie dostępnych rdzeni. Na przykład ustaw n = 0, aby umożliwić platformie automatyczne decydowanie o optymalnej liczbie procesów do uruchomienia w oparciu o środowisko.|
|**ResultsDirectory**||Katalog, w którym są umieszczane wyniki testów. Ścieżka jest określana względem katalogu, który zawiera plik. runsettings.|
|**TargetFrameworkVersion**|Framework40|`FrameworkCore10` w przypadku źródeł .NET Core dla `FrameworkUap10` źródeł opartych na platformy UWP, `Framework45` dla .NET Framework 4,5 i wyższych, `Framework40` dla .NET Framework 4,0 i `Framework35` .NET Framework 3,5.<br /><br />To ustawienie określa wersję struktury testów jednostkowych używanej do odnajdywania i wykonywania testów. Może ona być inna niż wersja platformy .NET określonej we właściwościach kompilacji projektu badania jednostki.<br /><br />W przypadku pominięcia `TargetFrameworkVersion` elementu z pliku *. runsettings* platforma automatycznie określa wersję platformy opartą na skompilowanych plikach binarnych.|
|**TargetPlatform**|x86|x86, x64|
|**TreatTestAdapterErrorsAsWarnings**|fałsz|fałsz, prawda|
|**TestAdaptersPaths**||Co najmniej jedna ścieżka do katalogu, w którym znajduje się TestAdapters|
|**TestSessionTimeout**||Umożliwia użytkownikom zakończenie sesji testowej, gdy przekroczy określony limit czasu. Ustawienie limitu czasu zapewnia, że zasoby są dobrze zużywane, a sesje testowe są ograniczone do określonego czasu. To ustawienie jest dostępne w programie **Visual Studio 2017 w wersji 15,5** lub nowszej.|
|**DotnetHostPath**||Określ ścieżkę niestandardową do hosta dotnet, który jest używany do uruchamiania testhost. Jest to przydatne podczas tworzenia własnego dotnet, na przykład podczas kompilowania repozytorium dotnet/Runtime. Określenie tej opcji spowoduje pominięcie wyszukiwania testhost.exe i zawsze będzie korzystać z testhost.dll. 

## <a name="datacollectors-element-diagnostic-data-adapters"></a>Elementy datacollects (adaptery danych diagnostycznych)

Element **Datacollects** określa ustawienia adapterów danych diagnostycznych. Adaptery danych diagnostycznych zbierają dodatkowe informacje o środowisku i testowanej aplikacji. Każda karta ma ustawienia domyślne i tylko wtedy, gdy nie chcesz używać ustawień domyślnych.

```xml
<DataCollectionRunSettings>
  <DataCollectors>
    <!-- data collectors -->
  </DataCollectors>
</DataCollectionRunSettings>
```

### <a name="codecoverage-data-collector"></a>Moduł zbierający dane CodeCoverage

Moduł zbierający dane pokrycia kodu tworzy dziennik z zapisami, które części kodu aplikacji zostały wykonane w teście. Aby uzyskać szczegółowe informacje o dostosowywaniu ustawień pokrycia kodu, zobacz [Dostosowywanie analizy pokrycia kodu](../test/customizing-code-coverage-analysis.md).

```xml
<DataCollector friendlyName="Code Coverage" uri="datacollector://Microsoft/CodeCoverage/2.0" assemblyQualifiedName="Microsoft.VisualStudio.Coverage.DynamicCoverageDataCollector, Microsoft.VisualStudio.TraceCollector, Version=11.0.0.0, Culture=neutral, PublicKeyToken=b03f5f7f11d50a3a">
  <Configuration>
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
  </CodeCoverage>
</Configuration>
```

### <a name="videorecorder-data-collector"></a>Moduł zbierający dane VideoRecorder

Moduł zbierający dane wideo przechwytuje nagrywanie ekranu, gdy testy są uruchamiane. To nagranie jest przydatne do rozwiązywania problemów z testami interfejsu użytkownika. Moduł zbierający dane wideo jest dostępny w programie **Visual Studio 2017 w wersji 15,5** lub nowszej. Przykład konfigurowania tego modułu zbierającego dane można znaleźć w [pliku example *. runsettings](#example-runsettings-file).

Aby dostosować każdy inny typ adapterów danych diagnostycznych, należy użyć [pliku ustawień testu](../test/collect-diagnostic-information-using-test-settings.md).

### <a name="blame-data-collector"></a>Moduł zbierający dane polecenia Blame

Ta opcja może pomóc wyizolować problematyczny test, który powoduje awarię hosta testowego. Uruchomienie modułu zbierającego tworzy plik wyjściowy (*Sequence.xml*) w *TestResults*, który przechwytuje kolejność wykonywania testu przed awarią. 

```xml
<DataCollector friendlyName="blame" enabled="True">
</DataCollector>
```

## <a name="testrunparameters"></a>TestRunParameters

```xml
<TestRunParameters>
    <Parameter name="webAppUrl" value="http://localhost" />
    <Parameter name="docsUrl" value="https://docs.microsoft.com" />
</TestRunParameters>
```

Parametry przebiegu testowego zapewniają sposób definiowania zmiennych i wartości, które są dostępne dla testów w czasie wykonywania. Uzyskaj dostęp do parametrów przy użyciu <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestContext.Properties%2A?displayProperty=nameWithType> właściwości MSTest (lub nunit [TestContext](https://docs.nunit.org/articles/nunit/writing-tests/TestContext.html)):

```csharp
private string _appUrl;
public TestContext TestContext { get; set; }

[TestMethod] // [Test] for NUnit
public void HomePageTest()
{
    string _appURL = TestContext.Properties["webAppUrl"];
}
```

Aby użyć parametrów przebiegu testowego, Dodaj <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestContext> Właściwość publiczną do klasy testowej.

## <a name="loggerrunsettings-element"></a>LoggerRunSettings, element

`LoggerRunSettings`Sekcja definiuje jeden lub więcej rejestratorów, które mają być używane dla przebiegu testu. Najbardziej typowymi rejestratorami są konsole, pliki programu Visual Studio Wyniki testów (TRX) i HTML.

```xml
<LoggerRunSettings>
    <Loggers>        
      <Logger friendlyName="console" enabled="True">
        <Configuration>
            <Verbosity>quiet</Verbosity>
        </Configuration>
      </Logger>
      <Logger friendlyName="trx" enabled="True">
        <Configuration>
          <LogFileName>foo.trx</LogFileName>
        </Configuration>
      </Logger>
      <Logger friendlyName="html" enabled="True">
        <Configuration>
          <LogFileName>foo.html</LogFileName>
        </Configuration>
      </Logger>
    </Loggers>
  </LoggerRunSettings>
```

## <a name="mstest-element"></a>MSTest, element

Te ustawienia są specyficzne dla adaptera testowego, który uruchamia metody testowe mające <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestMethodAttribute> atrybut.

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

|Konfiguracja|Domyślne|Wartości|
|-|-|-|
|**ForcedLegacyMode**|fałsz|W programie Visual Studio 2012 karta MSTest została zoptymalizowana tak, aby była szybsza i bardziej skalowalna. Niektóre zachowania, na przykład kolejność, w jakiej są uruchamiane testy, mogą nie być dokładnie takie same, jak w poprzednich wersjach programu Visual Studio. Ustaw tę wartość na **true** , aby użyć starszego adaptera testowego.<br /><br />Można na przykład użyć tego ustawienia, jeśli istnieje plik *app.config* określony dla testu jednostkowego.<br /><br />Zaleca się, aby rozważyć refaktoryzację testów pozwalającą na użycie nowszego adaptera.|
|**IgnoreTestImpact**|fałsz|Funkcja wpływu na testy określa priorytety testów, których dotyczą ostatnie zmiany, po uruchomieniu w MSTest lub z Microsoft Test Manager (przestarzałe w programie Visual Studio 2017). To ustawienie powoduje wyłączenie funkcji. Aby uzyskać więcej informacji, zobacz, [które testy należy uruchomić od poprzedniej kompilacji](https://msdn.microsoft.com/library/dd286589).|
|**SettingsFile**||W tym miejscu możesz określić plik ustawień testu, który ma być używany z kartą MSTest. Możesz również określić plik ustawień testu [w menu Ustawienia](#specify-a-run-settings-file-in-the-ide).<br /><br />Jeśli określisz tę wartość, musisz także ustawić **ForcedlegacyMode** na **true**.<br /><br />`<ForcedLegacyMode>true</ForcedLegacyMode>`|
|**KeepExecutorAliveAfterLegacyRun**|fałsz|Po zakończeniu przebiegu testu MSTest jest zamykany. Każdy proces, który jest uruchamiany jako część testu, również zostanie zamknięty. Jeśli chcesz zatrzymać program wykonujący testy, ustaw wartość na **true**. Można na przykład użyć tego ustawienia, aby zachować działanie przeglądarki między kodowanymi testami interfejsu użytkownika.|
|**DeploymentEnabled**|true|W przypadku ustawienia wartości **false**elementy wdrożenia określone w metodzie testowej nie są kopiowane do katalogu wdrożenia.|
|**CaptureTraceOutput**|true|Możesz pisać do śledzenia debugowania z metody testowej przy użyciu <xref:System.Diagnostics.Trace.WriteLine%2A?displayProperty=nameWithType> .|
|**DeleteDeploymentDirectoryAfterTestRunIsComplete**|true|Aby zachować katalog wdrożenia po przebiegu testu, należy ustawić tę wartość na **false**.|
|**MapInconclusiveToFailed**|fałsz|Jeśli test zakończy się nieniejednoznacznie, jest mapowany do stanu pominięty w **Eksploratorze testów**. Jeśli chcesz, aby testy niejednoznaczne były wyświetlane jako nieudane, ustaw wartość na **true**.|
|**InProcMode**|fałsz|Jeśli chcesz, aby testy były uruchamiane w tym samym procesie co karta MSTest, ustaw tę wartość na **true**. To ustawienie zapewnia mniejszy przyrost wydajności. Ale jeśli test kończy się wyjątkiem, pozostałe testy nie są uruchamiane.|
|**AssemblyResolution**|fałsz|Można określić ścieżki do dodatkowych zestawów podczas znajdowania i uruchamiania testów jednostkowych. Na przykład użyj tych ścieżek dla zestawów zależności, które nie znajdują się w tym samym katalogu, co zestaw testowy. Aby określić ścieżkę, użyj elementu **ścieżki katalogu** . Ścieżki mogą zawierać zmienne środowiskowe.<br /><br />`<AssemblyResolution>  <Directory Path="D:\myfolder\bin\" includeSubDirectories="false"/> </AssemblyResolution>`|

## <a name="example-runsettings-file"></a>Przykład pliku *. runsettings*

Poniższy kod XML przedstawia zawartość typowego pliku *. runsettings* . Skopiuj ten kod i zmodyfikuj go zgodnie z potrzebami.

Każdy element pliku jest opcjonalny, ponieważ ma wartość domyślną.

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

      <!-- Configuration for blame data collector -->
      <DataCollector friendlyName="blame" enabled="True">
      </DataCollector>

    </DataCollectors>
  </DataCollectionRunSettings>

  <!-- Parameters used by tests at run time -->
  <TestRunParameters>
    <Parameter name="webAppUrl" value="http://localhost" />
    <Parameter name="webAppUserName" value="Admin" />
    <Parameter name="webAppPassword" value="Password" />
  </TestRunParameters>
  
  <!-- Configuration for loggers -->
  <LoggerRunSettings>
    <Loggers>      
      <Logger friendlyName="console" enabled="True">
        <Configuration>
            <Verbosity>quiet</Verbosity>
        </Configuration>
      </Logger>
      <Logger friendlyName="trx" enabled="True">
        <Configuration>
          <LogFileName>foo.trx</LogFileName>
        </Configuration>
      </Logger>
      <Logger friendlyName="html" enabled="True">
        <Configuration>
          <LogFileName>foo.html</LogFileName>
        </Configuration>
      </Logger>
      <Logger friendlyName="blame" enabled="True" />
    </Loggers>
  </LoggerRunSettings>

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

## <a name="specify-environment-variables-in-the-runsettings-file"></a>Określanie zmiennych środowiskowych w pliku *. runsettings*

Zmienne środowiskowe można ustawić w pliku *runsettings* , który może bezpośrednio korzystać z hosta testowego. Określanie zmiennych środowiskowych w pliku *runsettings* jest niezbędne do obsługi nieuproszczonych projektów, które wymagają ustawienia zmiennych środowiskowych, takich jak *DOTNET_ROOT*. Te zmienne są ustawiane podczas duplikowania procesu hosta testowego i są dostępne na hoście.

### <a name="example"></a>Przykład

Poniższy kod to przykładowy plik *. runsettings* , który przekazuje zmienne środowiskowe:

```xml
<?xml version="1.0" encoding="utf-8"?>
<!-- File name extension must be .runsettings -->
<RunSettings>
  <RunConfiguration>
    <EnvironmentVariables>
      <!-- List of environment variables we want to set-->
      <DOTNET_ROOT>C:\ProgramFiles\dotnet</DOTNET_ROOT>
      <SDK_PATH>C:\Codebase\Sdk</SDK_PATH>
    </EnvironmentVariables>
  </RunConfiguration>
</RunSettings>
```

Węzeł **RunConfiguration** powinien zawierać węzeł **EnvironmentVariables** . Zmienna środowiskowa może być określona jako nazwa elementu i jego wartość.

> [!NOTE]
> Ponieważ te zmienne środowiskowe zawsze powinny być ustawiane podczas uruchamiania hosta testowego, testy powinny być zawsze uruchamiane w osobnym procesie. Dla tej flagi flaga */inisolation.* zostanie ustawiona, gdy istnieją zmienne środowiskowe, aby Host testowy był zawsze wywoływany.

## <a name="see-also"></a>Zobacz też

- [Konfigurowanie przebiegu testowego](https://github.com/microsoft/vstest-docs/blob/master/docs/configure.md)
- [Dostosowywanie analizy pokrycia kodu](../test/customizing-code-coverage-analysis.md)
- [Zadanie testowe programu Visual Studio (Azure Test Plans)](/azure/devops/pipelines/tasks/test/vstest?view=vsts)

