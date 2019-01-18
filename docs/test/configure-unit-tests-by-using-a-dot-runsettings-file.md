---
title: Konfigurowanie testów jednostkowych przy użyciu pliku .runsettings
ms.date: 02/28/2018
ms.prod: visual-studio-dev15
ms.topic: conceptual
ms.author: gewarren
manager: douge
ms.workload:
- multiple
author: gewarren
ms.openlocfilehash: 98e3de01bd5a12c842298ef6b923c232c0660977
ms.sourcegitcommit: 8bfabab73b39b3b3e68a3e8dc225515e8b310fed
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/18/2019
ms.locfileid: "54398276"
---
# <a name="configure-unit-tests-by-using-a-runsettings-file"></a>Konfigurowanie testów jednostkowych przy użyciu *.runsettings* pliku

Testy jednostkowe w programie Visual Studio, można skonfigurować za pomocą *.runsettings* pliku. Na przykład można zmienić wersji programu .NET Framework, na którym są uruchamiane testy, katalog dla wyników testów lub dane, które są zbierane podczas przebiegu testu.

Pliki parametrów uruchomieniowych są opcjonalne. Jeśli nie wymaga żadnej specjalnej konfiguracji, nie potrzebujesz *.runsettings* pliku. Najbardziej powszechnym zastosowaniem programu *.runsettings* plik jest w celu dostosowania [analiza pokrycia kodu](../test/customizing-code-coverage-analysis.md).

## <a name="specify-a-run-settings-file"></a>Określ plik parametrów uruchomieniowych

Ustawienia plików może służyć do konfigurowania testów, które są uruchamiane z przebiegu [wiersza polecenia](vstest-console-options.md), środowiska IDE lub w [utworzyć przepływ pracy](/azure/devops/pipelines/test/getting-started-with-continuous-testing?view=vsts) przy użyciu planów testowych platformy Azure lub Team Foundation Server (TFS).

### <a name="specify-a-run-settings-file-in-the-ide"></a>Określ plik parametrów uruchomieniowych w środowisku IDE

Wybierz **testu** > **ustawienia testu** > **zaznacz plik ustawień testu** , a następnie wybierz *.runsettings*pliku. Plik pojawi się na **ustawienia testu** menu, a można wybrać lub usunąć jej zaznaczenie. Zaznaczona, plik parametrów uruchomieniowych ma zastosowanie zawsze, gdy wybierzesz **Analizuj pokrycie kodu**.

![Wybierz menu Plik ustawień testu w programie Visual Studio](media/select-test-settings-file.png)

### <a name="specify-a-run-settings-file-at-the-command-line"></a>Określ plik parametrów uruchomieniowych w wierszu polecenia

Aby uruchomić testy z wiersza polecenia, użyj *vstest.console.exe* i określić plik ustawień za pomocą **Settings** parametru.

1. Uruchom wiersz polecenia programisty dla programu Visual Studio:

   Na Windows **Start** menu, wybierz **programu Visual Studio 2017** > **wiersz polecenia programisty dla programu VS 2017**.

2. Wprowadź polecenie podobne do:

   ```cmd
   vstest.console.exe MyTestAssembly.dll /EnableCodeCoverage /Settings:CodeCoverage.runsettings
   ```

Aby uzyskać więcej informacji, zobacz [opcje wiersza poleceń VSTest.Console.exe](vstest-console-options.md).

## <a name="customize-tests"></a>Dostosowywanie testów

Aby dostosować testy przy użyciu *.runsettings* plików, wykonaj następujące kroki:

1. Dodaj plik XML do rozwiązania programu Visual Studio i zapisz go jako *test.runsettings*.

   > [!TIP]
   > Nazwa pliku nie ma znaczenia, tak długo, jak używać rozszerzenia *.runsettings*.

1. Zastąp zawartość pliku XML z przykładu, który następuje po, a następnie go dostosowywać, odpowiednio do potrzeb.

1. Na **testu** menu, wybierz **ustawienia testu** > **zaznacz plik ustawień testu**. Przejdź do *.runsettings* utworzonego pliku, a następnie wybierz **OK**.

   > [!TIP]
   > Można utworzyć więcej niż jeden *.runsettings* plików w rozwiązaniu, a następnie wybierz jeden z nich jako aktywny plik ustawień testowych, zgodnie z potrzebami.

## <a name="example-runsettings-file"></a>Przykład *.runsettings* pliku

Następujący kody XML pokazuje zawartość typowej *.runsettings* pliku. Każdy element pliku jest opcjonalny, ponieważ ma on wartość domyślną.

```xml
<?xml version="1.0" encoding="utf-8"?>
<RunSettings>
  <!-- Configurations that affect the Test Framework -->
  <RunConfiguration>
    <MaxCpuCount>1</MaxCpuCount>
    <!-- Path relative to solution directory -->
    <ResultsDirectory>.\TestResults</ResultsDirectory>

    <!-- x86 or x64 -->
    <!-- You can also change it from the top-level menu Test > Test Settings > Processor Architecture for AnyCPU Projects -->
    <TargetPlatform>x86</TargetPlatform>

    <!-- Framework35 | [Framework40] | Framework45 -->
    <TargetFrameworkVersion>Framework40</TargetFrameworkVersion>

    <!-- Path to Test Adapters -->
    <TestAdaptersPaths>%SystemDrive%\Temp\foo;%SystemDrive%\Temp\bar</TestAdaptersPaths>

    <!-- TestSessionTimeout is only available with Visual Studio 2017 version 15.5 and higher -->
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
        <!--Video data collector is only available with Visual Studio 2017 version 15.5 and higher -->
      </DataCollector>

    </DataCollectors>
  </DataCollectionRunSettings>

  <!-- Parameters used by tests at runtime -->
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

## <a name="elements-of-a-runsettings-file"></a>Elementy *.runsettings* pliku

W kolejnych sekcjach szczegółowo elementy *.runsettings* pliku.

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

**RunConfiguration** element może zawierać następujące elementy:

|Węzeł|Domyślny|Wartości|
|-|-|-|
|**ResultsDirectory**||Katalog, w którym są umieszczane wyniki testu.|
|**TargetFrameworkVersion**|Framework40|Framework35, Framework40, Framework45<br /><br />To ustawienie określa wersję środowiska testów jednostkowych, które są używane do odnajdowania i wykonywania testów. Może ona być inna niż wersja platformy .NET określonej we właściwościach kompilacji projektu badania jednostki.|
|**TargetPlatform**|x86|x86, x64|
|**TreatTestAdapterErrorsAsWarnings**|false|fałsz, prawda|
|**TestAdaptersPaths**||Jedną lub więcej ścieżek do katalogu, w którym znajdują się TestAdapters|
|**MaxCpuCount**|1|To ustawienie kontrolki stopień równoległe wykonywanie testów, gdy Uruchamianie testów jednostek, przy użyciu dostępnych rdzeni na maszynie. Aparatu wykonywania testów jest uruchamiana jako osobnego procesu na każdym dostępnym rdzeniu i zapewnia każdego rdzenia kontenera za pomocą testów do uruchomienia. Kontener może być zestaw, biblioteki DLL lub odpowiedniego artefaktu. Kontener testu jest jednostką planowania. W każdym kontenerze testy są uruchamiane zgodnie ze struktury testowej. Jeśli istnieje wiele kontenerów, następnie jako przetwarza zakończenia wykonywania testów w kontenerze mają one następny dostępny kontener.<br /><br />Może być MaxCpuCount:<br /><br />n, gdzie 1 < = n < = liczba rdzeni: maksymalnie n procesy są uruchomione<br /><br />n, gdzie n = dowolna inna wartość: liczba uruchomionych procesów może zawierać maksymalnie liczbę dostępnych rdzeni|
|**TestSessionTimeout**||Umożliwia użytkownikom zakończyć sesję testową, gdy przekracza ona danego limitu czasu. Ustawienie limitu czasu zapewnia, że zasoby są również używane i sesje testów są ograniczone do określonym czasie. To ustawienie jest dostępne w **programu Visual Studio 2017 w wersji 15.5** i nowszych.|

### <a name="diagnostic-data-adapters-data-collectors"></a>Adaptery danych diagnostycznych (kolektory danych)

**DataCollectors** element określa ustawienia adapterów danych diagnostycznych. Adaptery danych diagnostycznych zbierać dodatkowe informacje na temat środowiska i testowanej aplikacji. Każdy adapter ma ustawienia domyślne, a następnie trzeba podać ustawienia, jeśli nie chcesz użyć wartości domyślnych.

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

Moduł zbierający dane pokrycia kodu tworzy dziennik z zapisami, które części kodu aplikacji zostały wykonane w teście. Aby uzyskać więcej informacji o dostosowywaniu ustawień pokrycia kodu, zobacz [Dostosowywanie analizy pokrycia kodu](../test/customizing-code-coverage-analysis.md).

#### <a name="video-data-collector"></a>Moduł zbierający dane wideo

Moduł zbierający dane wideo przechwytuje rejestrowania ekranu, gdy testy są uruchamiane. To nagranie jest przydatne podczas rozwiązywania problemów testy interfejsu użytkownika. Moduł zbierający dane wideo jest dostępna w **programu Visual Studio 2017 w wersji 15.5** i nowszych.

Aby dostosować każdy inny rodzaj adapterów danych diagnostycznych, należy użyć [pliku ustawień testu](../test/collect-diagnostic-information-using-test-settings.md).

### <a name="testrunparameters"></a>TestRunParameters

```xml
<TestRunParameters>
    <Parameter name="webAppUrl" value="http://localhost" />
    <Parameter name="webAppUserName" value="Admin" />
    <Parameter name="webAppPassword" value="Password" />
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

Aby użyć parametrów przebiegu testu, Dodaj prywatnej <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestContext> pola i publiczny <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestContext> właściwości do klasy testowej.

### <a name="mstest-run-settings"></a>MSTest parametrów uruchomieniowych

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

Te ustawienia są właściwe dla adaptera testowego, który uruchamia metody testowe, które mają <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestMethodAttribute> atrybutu.

|Konfiguracja|Domyślny|Wartości|
|-|-|-|
|**ForcedLegacyMode**|false|W programie Visual Studio 2012 Adapter karty MSTest został zoptymalizowany umożliwiają szybsze i bardziej skalowalne. Niektóre zachowania, na przykład kolejność, w jakiej są uruchamiane testy, mogą nie być dokładnie takie same, jak w poprzednich wersjach programu Visual Studio. Ustaw tę wartość na **true** Aby użyć starszego adaptera testowego.<br /><br />Na przykład możesz użyć tego ustawienia, jeśli masz *app.config* plik określony dla testu jednostkowego.<br /><br />Zaleca się, aby rozważyć refaktoryzację testów pozwalającą na użycie nowszego adaptera.|
|**IgnoreTestImpact**|false|Funkcja wpływu na testy określa priorytety testów, których dotyczą ostatnie zmiany, po uruchomieniu w programie MSTest lub Microsoft Test Manager. To ustawienie powoduje wyłączenie funkcji. Aby uzyskać więcej informacji, zobacz [testy, które można uruchamiać od czasu poprzedniej kompilacji](https://msdn.microsoft.com/library/dd286589).|
|**SettingsFile**||Można określić plik ustawień testu do użycia przez adapter MSTest. Można również określić plik ustawień testu, wybierając **Test** > **ustawienia testu** > **wybierz plik ustawień testu**.<br /><br />Jeśli ta wartość jest podana, należy także ustawić **ForcedlegacyMode** do **true**.<br /><br />`<ForcedLegacyMode>true</ForcedLegacyMode>`|
|**KeepExecutorAliveAfterLegacyRun**|false|Po zakończeniu przebiegu testu MSTest jest zamykany. Żaden proces, który jest uruchamiany jako część testu jest także skasowane. Jeśli chcesz utrzymać aktywność modułu wykonania testu, ustaw wartość **true**. Na przykład można użyć tego ustawienia do zachowania działania przeglądarki między kodowane testy interfejsu użytkownika.|
|**DeploymentEnabled**|true|Jeśli wartość jest ustawiona na **false**, elementy wdrożenia, które zostały określone w metodzie testowej, nie są kopiowane do katalogu wdrażania.|
|**CaptureTraceOutput**|true|Można zapisywać do śledzenia debugowania z metody testu przy użyciu <xref:System.Diagnostics.Trace.WriteLine%2A?displayProperty=nameWithType>.|
|**DeleteDeploymentDirectoryAfterTestRunIsComplete**|true|Aby zachować deployment directory po przebiegu testu, ustaw tę wartość na **false**.|
|**MapInconclusiveToFailed**|false|Jeśli test zakończy się ze stanem niejednoznaczny, jest mapowany do stanu pominięto w **Eksploratora testów**. Jeśli chcesz, aby testy niejednoznaczne być pokazywany jako zakończony niepowodzeniem, ustaw wartość **true**.|
|**InProcMode**|false|Jeśli chcesz, aby testy będą uruchamiane w tym samym procesie co MSTest adapter, ustaw tę wartość na **true**. To ustawienie zapewnia mniejszy przyrost wydajności. Ale jeśli test kończy się z powodu wyjątku, pozostałe testy nie działa.|
|**AssemblyResolution**|false|Można określić ścieżki do dodatkowych zestawów, podczas znajdowania i uruchamiania testów jednostkowych. Na przykład użyj tych ścieżek dla zestawów zależności, które nie znajdują się w tym samym katalogu co zestaw testów. Aby określić ścieżkę, należy użyć **ścieżkę katalogu** elementu. Ścieżki może zawierać zmienne środowiskowe.<br /><br />`<AssemblyResolution>  <Directory Path="D:\myfolder\bin\" includeSubDirectories="false"/> </AssemblyResolution>`|

## <a name="see-also"></a>Zobacz także

- [Dostosowywanie analizy pokrycia kodu](../test/customizing-code-coverage-analysis.md)
- [Visual Studio test zadań (plany testów platformy Azure)](/azure/devops/pipelines/tasks/test/vstest?view=vsts)
