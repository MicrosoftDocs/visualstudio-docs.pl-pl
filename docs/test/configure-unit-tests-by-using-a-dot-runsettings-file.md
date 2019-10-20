---
title: Konfigurowanie testów jednostkowych przy użyciu pliku. runsettings
ms.date: 06/14/2019
ms.topic: conceptual
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
author: jillre
ms.openlocfilehash: 22fe1de176819807c5cd60d746f381e325601799
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72665139"
---
# <a name="configure-unit-tests-by-using-a-runsettings-file"></a>Konfigurowanie testów jednostkowych przy użyciu pliku *. runsettings*

Testy jednostkowe w programie Visual Studio można skonfigurować przy użyciu pliku *. runsettings* . Na przykład można zmienić wersję platformy .NET, w której testy są uruchamiane, katalog dla wyników testu lub dane, które są zbierane podczas przebiegu testowego.

Pliki parametrów uruchomieniowych są opcjonalne. Jeśli nie jest wymagana żadna specjalna konfiguracja, nie jest potrzebny plik *. runsettings* . Typowym zastosowaniem pliku *. runsettings* jest dostosowanie [analizy pokrycia kodu](../test/customizing-code-coverage-analysis.md).

## <a name="specify-a-run-settings-file"></a>Określ plik parametrów uruchomieniowych

Pliki parametrów uruchomieniowych mogą służyć do konfigurowania testów uruchamianych z [wiersza polecenia](vstest-console-options.md)w środowisku IDE lub w [przepływie pracy kompilacji](/azure/devops/pipelines/test/getting-started-with-continuous-testing?view=vsts) przy użyciu Azure test PLANS lub Team Foundation Server (TFS).

### <a name="ide"></a>IDE

::: moniker range="vs-2017"

Aby określić plik parametrów uruchomieniowych w środowisku IDE, wybierz pozycję **testuj** > **Ustawienia testu** > **Wybierz plik ustawień testu**, a następnie wybierz plik *. runsettings* .

![Wybieranie menu plik ustawień testu w programie Visual Studio 2017](media/select-test-settings-file.png)

Plik jest wyświetlany w menu Ustawienia testu i można go zaznaczyć lub usunąć jego zaznaczenie. Gdy jest zaznaczone, plik parametrów uruchomieniowych ma zastosowanie zawsze, gdy wybierzesz opcję **Analizuj pokrycie kodu**.

::: moniker-end

::: moniker range=">=vs-2019"

Aby określić plik parametrów uruchomieniowych w środowisku IDE, wybierz pozycję **testuj**  > **Wybierz plik ustawień**. Przejdź do pliku *. runsettings* i wybierz go.

![Wybieranie menu plik ustawień testu w programie Visual Studio 2019](media/vs-2019/select-settings-file.png)

Plik jest wyświetlany w menu test i można go zaznaczyć lub usunąć jego zaznaczenie. Gdy jest zaznaczone, plik parametrów uruchomieniowych ma zastosowanie zawsze, gdy wybierzesz opcję **Analizuj pokrycie kodu**.

::: moniker-end

### <a name="command-line"></a>Wiersz polecenia

Aby uruchomić testy z wiersza polecenia, należy użyć *VSTest. Console. exe*i określić plik ustawień przy użyciu parametru **/Settings** .

1. Uruchom wiersz polecenia programisty dla programu Visual Studio:

   ::: moniker range="vs-2017"

   W menu **Start** systemu Windows wybierz pozycję **Visual Studio 2017** > **wiersz polecenia dla deweloperów dla programu vs 2017**.

   ::: moniker-end

   ::: moniker range=">=vs-2019"

   W menu **Start** systemu Windows wybierz pozycję **Visual Studio 2019** > **wiersz polecenia dla deweloperów dla programu vs 2019**.

   ::: moniker-end

2. Wprowadź polecenie podobne do:

   ```cmd
   vstest.console.exe MyTestAssembly.dll /EnableCodeCoverage /Settings:CodeCoverage.runsettings
   ```

   lub

   ```cmd
   vstest.console.exe --settings:test.runsettings test.dll
   ```

Aby uzyskać więcej informacji, zobacz [Opcje wiersza polecenia VSTest. Console. exe](vstest-console-options.md).

## <a name="customize-tests"></a>Dostosowywanie testów

Aby dostosować testy przy użyciu pliku *. runsettings* , wykonaj następujące kroki:

1. Dodaj plik XML do rozwiązania Visual Studio i Zapisz go jako *test. runsettings*.

   > [!TIP]
   > Nazwa pliku nie ma znaczenia, o ile używasz rozszerzenia *runsettings*.

2. Zamień zawartość pliku na kod XML z poniższego przykładu i dostosuj go zgodnie z wymaganiami.

::: moniker range="vs-2017"

3. W menu **test** wybierz pozycję **Ustawienia testu**  > **Wybierz plik ustawień testu**. Przejdź do utworzonego pliku *runsettings* , a następnie wybierz przycisk **OK**.

::: moniker-end

::: moniker range=">=vs-2019"

3. Aby wybrać plik parametrów uruchomieniowych, wybierz opcję **testuj**  > **Wybierz plik ustawień**. Przejdź do utworzonego pliku *runsettings* , a następnie wybierz przycisk **OK**.

::: moniker-end

   > [!TIP]
   > W rozwiązaniu można utworzyć więcej niż jeden plik *. runsettings* i wybrać jeden z nich jako aktywny plik ustawień testu.

## <a name="example-runsettings-file"></a>Przykład pliku *. runsettings*

Poniższy kod XML przedstawia zawartość typowego pliku *. runsettings* . Każdy element pliku jest opcjonalny, ponieważ ma wartość domyślną.

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

## <a name="elements-of-a-runsettings-file"></a>Elementy pliku *. runsettings*

Poniższe sekcje zawierają szczegółowe informacje o elementach pliku *. runsettings* .

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

Element **RunConfiguration** może zawierać następujące elementy:

|Węzeł|Domyślny|Wartości|
|-|-|-|
|**ResultsDirectory**||Katalog, w którym są umieszczane wyniki testów.|
|**TargetFrameworkVersion**|Framework40|`FrameworkCore10` dla źródeł .NET Core `FrameworkUap10` dla źródeł opartych na platformy UWP `Framework45` dla .NET Framework 4,5 i wyższych, `Framework40` .NET Framework 4,0 i `Framework35` .NET Framework 3,5.<br /><br />To ustawienie określa wersję struktury testów jednostkowych używanej do odnajdywania i wykonywania testów. Może ona być inna niż wersja platformy .NET określonej we właściwościach kompilacji projektu badania jednostki.<br /><br />W przypadku pominięcia `TargetFrameworkVersion` elementu z pliku *. runsettings* platforma automatycznie określi wersję platformy opartą na skompilowanych plikach binarnych.|
|**TargetPlatform**|x86|x86, x64|
|**TreatTestAdapterErrorsAsWarnings**|false|fałsz, prawda|
|**TestAdaptersPaths**||Co najmniej jedna ścieżka do katalogu, w którym znajduje się TestAdapters|
|**MaxCpuCount**|1|To ustawienie określa stopień równoległego wykonywania testów podczas uruchamiania testów jednostkowych przy użyciu dostępnych rdzeni na komputerze. Aparat wykonywania testu jest uruchamiany jako proces odrębny dla każdego dostępnego rdzenia i zapewnia każdy rdzeń kontenera z testami do uruchomienia. Kontener może być zestawem, biblioteką DLL lub odpowiednim artefaktem. Kontener testowy jest jednostką planowania. W każdym kontenerze testy są uruchamiane zgodnie z platformą testową. Jeśli istnieje wiele kontenerów, a następnie procesy ukończyą wykonywanie testów w kontenerze, otrzymają następny dostępny kontener.<br /><br />MaxCpuCount może:<br /><br />n, gdzie 1 < = n < = liczba rdzeni: uruchomiono do n procesów<br /><br />n, gdzie n = jakakolwiek inna wartość: liczba uruchomionych procesów może być równa liczbie dostępnych rdzeni|
|**TestSessionTimeout**||Umożliwia użytkownikom zakończenie sesji testowej, gdy przekroczy określony limit czasu. Ustawienie limitu czasu zapewnia, że zasoby są dobrze zużywane, a sesje testowe są ograniczone do określonego czasu. To ustawienie jest dostępne w programie **Visual Studio 2017 w wersji 15,5** lub nowszej.|

### <a name="diagnostic-data-adapters-data-collectors"></a>Adaptery danych diagnostycznych (moduły zbierające dane)

Element **Datacollects** określa ustawienia adapterów danych diagnostycznych. Adaptery danych diagnostycznych zbierają dodatkowe informacje o środowisku i testowanej aplikacji. Każda karta ma ustawienia domyślne i tylko wtedy, gdy nie chcesz używać ustawień domyślnych.

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

Moduł zbierający dane wideo przechwytuje nagrywanie ekranu, gdy testy są uruchamiane. To nagranie jest przydatne do rozwiązywania problemów z testami interfejsu użytkownika. Moduł zbierający dane wideo jest dostępny w programie **Visual Studio 2017 w wersji 15,5** lub nowszej.

Aby dostosować każdy inny typ adapterów danych diagnostycznych, należy użyć [pliku ustawień testu](../test/collect-diagnostic-information-using-test-settings.md).

### <a name="testrunparameters"></a>TestRunParameters

```xml
<TestRunParameters>
    <Parameter name="webAppUrl" value="http://localhost" />
    <Parameter name="docsUrl" value="https://docs.microsoft.com" />
</TestRunParameters>
```

Parametry przebiegu testowego zapewniają sposób definiowania zmiennych i wartości, które są dostępne dla testów w czasie wykonywania. Uzyskaj dostęp do parametrów przy użyciu właściwości <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestContext.Properties%2A?displayProperty=nameWithType>:

```csharp
[TestMethod]
public void HomePageTest()
{
    string appURL = TestContext.Properties["webAppUrl"];
}
```

Aby użyć parametrów przebiegu testowego, Dodaj prywatne pole <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestContext> i publiczną właściwość <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestContext> do klasy testowej.

### <a name="mstest-run-settings"></a>MSTest Parametry uruchomieniowe

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

Te ustawienia są specyficzne dla adaptera testowego, który uruchamia metody testowe mające atrybut <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestMethodAttribute>.

|Konfiguracja|Domyślny|Wartości|
|-|-|-|
|**ForcedLegacyMode**|false|W programie Visual Studio 2012 karta MSTest została zoptymalizowana tak, aby była szybsza i bardziej skalowalna. Niektóre zachowania, na przykład kolejność, w jakiej są uruchamiane testy, mogą nie być dokładnie takie same, jak w poprzednich wersjach programu Visual Studio. Ustaw tę wartość na **true** , aby użyć starszego adaptera testowego.<br /><br />Można na przykład użyć tego ustawienia, jeśli masz plik *App. config* określony dla testu jednostkowego.<br /><br />Zaleca się, aby rozważyć refaktoryzację testów pozwalającą na użycie nowszego adaptera.|
|**IgnoreTestImpact**|false|Funkcja wpływu na testy określa priorytety testów, których dotyczą ostatnie zmiany, po uruchomieniu w programie MSTest lub Microsoft Test Manager. To ustawienie powoduje wyłączenie funkcji. Aby uzyskać więcej informacji, zobacz, [które testy należy uruchomić od poprzedniej kompilacji](https://msdn.microsoft.com/library/dd286589).|
|**SettingsFile**||W tym miejscu możesz określić plik ustawień testu, który ma być używany z kartą MSTest. Możesz również określić plik ustawień testu [w menu Ustawienia](#ide).<br /><br />Jeśli określisz tę wartość, musisz także ustawić **ForcedlegacyMode** na **true**.<br /><br />`<ForcedLegacyMode>true</ForcedLegacyMode>`|
|**KeepExecutorAliveAfterLegacyRun**|false|Po zakończeniu przebiegu testu MSTest jest zamykany. Każdy proces, który jest uruchamiany jako część testu, również zostanie zamknięty. Jeśli chcesz zatrzymać program wykonujący testy, ustaw wartość na **true**. Można na przykład użyć tego ustawienia, aby zachować działanie przeglądarki między kodowanymi testami interfejsu użytkownika.|
|**DeploymentEnabled**|true|W przypadku ustawienia wartości **false**elementy wdrożenia określone w metodzie testowej nie są kopiowane do katalogu wdrożenia.|
|**CaptureTraceOutput**|true|Można pisać do śledzenia debugowania z metody testowej przy użyciu <xref:System.Diagnostics.Trace.WriteLine%2A?displayProperty=nameWithType>.|
|**DeleteDeploymentDirectoryAfterTestRunIsComplete**|true|Aby zachować katalog wdrożenia po przebiegu testu, należy ustawić tę wartość na **false**.|
|**MapInconclusiveToFailed**|false|Jeśli test zakończy się nieniejednoznacznie, jest mapowany do stanu pominięty w **Eksploratorze testów**. Jeśli chcesz, aby testy niejednoznaczne były wyświetlane jako nieudane, ustaw wartość na **true**.|
|**Inprocmode**|false|Jeśli chcesz, aby testy były uruchamiane w tym samym procesie co karta MSTest, ustaw tę wartość na **true**. To ustawienie zapewnia mniejszy przyrost wydajności. Ale jeśli test kończy się wyjątkiem, pozostałe testy nie są uruchamiane.|
|**AssemblyResolution**|false|Można określić ścieżki do dodatkowych zestawów podczas znajdowania i uruchamiania testów jednostkowych. Na przykład użyj tych ścieżek dla zestawów zależności, które nie znajdują się w tym samym katalogu, co zestaw testowy. Aby określić ścieżkę, użyj elementu **ścieżki katalogu** . Ścieżki mogą zawierać zmienne środowiskowe.<br /><br />`<AssemblyResolution>  <Directory Path="D:\myfolder\bin\" includeSubDirectories="false"/> </AssemblyResolution>`|

## <a name="see-also"></a>Zobacz także

- [Konfigurowanie przebiegu testowego](https://github.com/microsoft/vstest-docs/blob/master/docs/configure.md)
- [Dostosowywanie analizy pokrycia kodu](../test/customizing-code-coverage-analysis.md)
- [Zadanie testowe programu Visual Studio (Azure Test Plans)](/azure/devops/pipelines/tasks/test/vstest?view=vsts)
