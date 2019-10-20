---
title: Konfigurowanie testów jednostkowych przy użyciu pliku. runsettings | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-test
ms.topic: conceptual
ms.assetid: f7e9e4a2-5d01-4f78-b408-5be3892bd162
caps.latest.revision: 28
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: b9779dd685ad662cd0761dc85be58d0dbb3ccf0c
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72660657"
---
# <a name="configure-unit-tests-by-using-a-runsettings-file"></a>Konfigurowanie testów jednostkowych przy użyciu pliku runsettings
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Testy jednostkowe w programie Visual Studio można skonfigurować przy użyciu pliku *. runsettings. (Nazwa pliku nie ma znaczenia, pod warunkiem, że używasz rozszerzenia ". runsettings.") Na przykład można zmienić .NET Framework, na którym będą uruchamiane testy, katalog, w którym są dostarczane wyniki testów oraz dane zbierane podczas przebiegu testowego.

 Jeśli nie chcesz wykonywać żadnej specjalnej konfiguracji, nie potrzebujesz pliku *. runsettings. Najczęstszym zastosowaniem jest dostosowanie [pokrycia kodu](../test/customizing-code-coverage-analysis.md).

> [!NOTE]
> **. runsettings i. testsettings**
>
> Istnieją dwa typy plików do konfiguracji testów. *. runsettings są używane do testów jednostkowych. I \*. testsettings dla [testów środowiska laboratoryjnego](https://msdn.microsoft.com/library/0c15317e-80c6-4317-aed3-82b8e15e3901), testów wydajności sieci Web i obciążenia oraz do dostosowywania niektórych typów adapterów danych diagnostycznych, takich jak IntelliTrace i karty dziennika zdarzeń.
>
> W poprzednich wersjach programu Visual Studio o wartości do 2010 testy jednostkowe zostały również dostosowane przy użyciu plików *. testsettings. Nadal możesz to zrobić, ale testy będą działać wolniej niż w przypadku używania równoważnych konfiguracji w pliku \*. runsettings.

## <a name="customizing-tests-with-a-runsettings-file"></a>Dostosowywanie testów przy użyciu pliku .runsettings

1. Dodaj plik XML do rozwiązania programu Visual Studio i zmień jego nazwę na test. runsettings. (Nazwa pliku nie ma znaczenia, ale rozszerzenie musi mieć wartość. runsettings.)

2. Zastąp zawartość pliku [przykładem](#example).

    Zmodyfikuj go według własnych potrzeb.

3. W menu **test** wybierz **Ustawienia testu**, **Wybierz plik ustawień testu**.

   W rozwiązaniu można utworzyć więcej niż jeden plik \*. runsettings, a następnie włączyć lub wyłączyć je w różnych godzinach przy użyciu menu **Ustawienia testu** .

   ![Włączanie pliku parametrów uruchomieniowych](../test/media/runsettings-1.png "RunSettings-1")

## <a name="example"></a>Skopiuj ten przykładowy plik. runsettings
 Oto typowy plik *. runsettings. Każdy element pliku jest opcjonalny, ponieważ każda wartość ma domyślne parametry.

```xml
<?xml version="1.0" encoding="utf-8"?>
<RunSettings>
  <!-- Configurations that affect the Test Framework -->
  <RunConfiguration>
    <MaxCpuCount>1</MaxCpuCount>
    <!-- Path relative to solution directory -->
    <ResultsDirectory>.\TestResults</ResultsDirectory>

    <!-- [x86] | x64
      - You can also change it from menu Test, Test Settings, Default Processor Architecture -->
    <TargetPlatform>x86</TargetPlatform>

    <!-- Framework35 | [Framework40] | Framework45 -->
    <TargetFrameworkVersion>Framework40</TargetFrameworkVersion>

    <!-- Path to Test Adapters -->
    <TestAdaptersPaths>%SystemDrive%\Temp\foo;%SystemDrive%\Temp\bar</TestAdaptersPaths>
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

 Plik. runsettings jest również używany do konfigurowania [pokrycia kodu](../test/customizing-code-coverage-analysis.md).

 W pozostałej części tego tematu opisano zawartość pliku.

## <a name="edit-your-runsettings-file"></a>Edytuj plik .runsettings
 Plik .runsettings zawiera poniższe elementy.

### <a name="test-run-configuration"></a>Konfiguracja przebiegu testowego

|Węzeł|Domyślny|Wartości|
|----------|-------------|------------|
|`ResultsDirectory`||Katalog, w którym zostaną umieszczone wyniki testu.|
|`TargetFrameworkVersion`|Framework40|Framework35, Framework40, Framework45<br /><br /> Określa, która wersja środowiska testów jednostkowych jest używana do odnajdowania i wykonywania testów. Może ona być inna niż wersja platformy .NET określonej we właściwościach kompilacji projektu badania jednostki.|
|`TargetPlatform`|x86|x86, x64|
|`TreatTestAdapterErrorsAsWarnings`|false|fałsz, prawda|
|`TestAdaptersPaths`||Jedna lub wiele ścieżek do katalogu, w którym znajdują się TestAdapters|
|`MaxCpuCount`|1|Kontroluje to stopień równoległego wykonywania testów podczas uruchamiania testów jednostkowych przy użyciu dostępnych rdzeni na komputerze.  Aparat wykonywania testu jest uruchamiany jako proces odrębny dla każdego dostępnego rdzenia i zapewnia każdy rdzeń kontenera z testami do uruchomienia, taki jak zestaw, DLL lub odpowiedni artefakt.  Kontener testowy jest jednostką planowania.  W każdym kontenerze testy są uruchamiane zgodnie z platformą testową.  W przypadku wielu kontenerów, gdy procesy zakończą wykonywanie testów w kontenerze, otrzymają następny dostępny kontener.<br /><br /> MaxCpuCount może:<br /><br /> n, gdzie 1 < = n < = liczba rdzeni: zostanie uruchomionych maksymalnie n procesów<br /><br /> n, gdzie n = jakakolwiek inna wartość: liczba uruchomionych procesów będzie równa tylu rdzeniom na komputerze|

### <a name="diagnostic-data-adapters-data-collectors"></a>Adaptery danych diagnostycznych (kolektory danych)
 Element `DataCollectors` określa ustawienia adapterów danych diagnostycznych. Adaptery danych diagnostycznych są używane do zbierania dodatkowych informacji dotyczących środowiska i testowanej aplikacji. Każdy adapter ma ustawienia domyślne, dlatego ustawienia trzeba podać tylko wtedy, gdy nie chce się używać tych domyślnych.

#### <a name="code-coverage-adapter"></a>Adapter pokrycia kodu
 Moduł zbierający dane pokrycia kodu tworzy dziennik z zapisami, które części kodu aplikacji zostały wykonane w teście. Aby uzyskać więcej informacji o dostosowywaniu ustawień pokrycia kodu, zobacz [Dostosowywanie analizy pokrycia kodu](../test/customizing-code-coverage-analysis.md).

#### <a name="other-diagnostic-data-adapters"></a>Inne adaptery danych diagnostycznych
 Adapter pokrycia kodu jest obecnie jedynym adapterem, który można dostosować przy użyciu pliku parametrów uruchomieniowych.

 Aby dostosować każdy inny rodzaj adaptera danych diagnostycznych, należy użyć pliku ustawień testu. Aby uzyskać więcej informacji, zobacz [Określanie ustawień testu dla testów programu Visual Studio](https://msdn.microsoft.com/library/0c15317e-80c6-4317-aed3-82b8e15e3901).

#### <a name="testrunparameters"></a>TestRunParameters
 TestRunParameters zapewnia sposób definiowania zmiennych i wartości, które są dostępne dla testów w czasie wykonywania.

### <a name="mstest-run-settings"></a>Ustawienia wykonywania MSTest
 Te ustawienia są specyficzne dla adaptera testowego, który uruchamia metody testowe mające atrybut `[TestMethod]`.

|Konfiguracja|Domyślny|Wartości|
|-------------------|-------------|------------|
|ForcedLegacyMode|false|W programie Visual Studio 2012 adapter karty MSTest został zoptymalizowany, aby był bardziej skalowalny i działał szybciej. Niektóre zachowania, na przykład kolejność, w jakiej są uruchamiane testy, mogą nie być dokładnie takie same, jak w poprzednich wersjach programu Visual Studio. Ustaw tę wartość `true`, aby użyć starszego adaptera testowego.<br /><br /> Można jej użyć na przykład wtedy, gdy dysponujesz plikiem app.config określonym dla testu jednostkowego.<br /><br /> Zaleca się, aby rozważyć refaktoryzację testów pozwalającą na użycie nowszego adaptera.|
|IgnoreTestImpact|false|Funkcja wpływu na testy określa priorytety testów, których dotyczą ostatnie zmiany, po uruchomieniu w programie MSTest lub Microsoft Test Manager. To ustawienie powoduje wyłączenie funkcji. Aby uzyskać więcej informacji, zobacz [jak: zbierać dane, aby sprawdzić, które testy powinny być uruchamiane po zmianie kodu](https://msdn.microsoft.com/library/2f921ea1-9bb0-4870-a30f-0521fc22cb47).|
|SettingsFile||Można tu określić plik ustawień testowych do użycia z adapterem MS Test. Możesz również określić plik ustawień testu przy użyciu menu **test**, **Ustawienia testu**, **Wybierz plik ustawień testu**.<br /><br /> Jeśli określisz tę wartość, musisz także ustawić **ForcedlegacyMode** na **true**.<br /><br /> `<RunSettings>   <MSTest>     <SettingsFile>my.testsettings</SettingsFile>      <ForcedLegacyMode>true</ForcedLegacyMode>    </MSTest> </RunSettings>`|
|KeepExecutorAliveAfterLegacyRun|false|Po zakończeniu przebiegu testu MSTest jest zamykany. Każdy proces, który jest uruchamiany jako część testu, również będzie w tej chwili zatrzymywany. Jeśli program wykonujący test ma być nadal aktywny, ustaw dla tej konfiguracji wartość true.<br /><br /> Można na przykład wykorzystać ją do zachowania działania przeglądarki między kodowanymi testami interfejsu użytkownika.|
|DeploymentEnabled|true|Jeśli zostanie ustawiona wartość false, elementy wdrożenia, które określono w metodzie testowej, nie zostaną skopiowane do katalogu wdrożenia.|
|CaptureTraceOutput|true|Można zapisywać do śledzenia debugowania ze swojej metody testowej przy użyciu Trace.WriteLine. Za pomocą tej konfiguracji można wyłączyć ślady debugowania.|
|DeleteDeploymentDirectoryAfterTestRunIsComplete|true|Można zachować Deployment Directory po przebiegu testu z ustawieniem tej wartości jako fałszywej.|
|MapInconclusiveToFailed|false|Jeśli test jest zwracany ze stanem Niejednoznaczny, zwykle będzie mapowany do stanu Pominięty w Eksploratorze testów. Jeśli chcesz, aby testy niejednoznaczne były wykazywane jako Zakończone niepowodzeniem, użyj tej konfiguracji.|
|InProcMode|false|Jeśli testy mają być wykonywane w tym samym procesie co adapter MS Test, dla wartości tej należy wybrać ustawienie true. To ustawienie zapewnia mniejszy przyrost wydajności. Jeśli jednak test kończy się wyjątkiem, inne testy nie będą kontynuowane.|
|AssemblyResolution|false|Można określić ścieżki do dodatkowych zestawów podczas znajdowania i uruchamiania testów jednostkowych.  Na przykład użyj tych ścieżek dla zestawów zależności, które nie znajdują się w tym samym katalogu, co zestaw testowy.  Aby określić ścieżkę, użyj elementu "ścieżka katalogu".  Ścieżki mogą zawierać zmienne środowiskowe.<br /><br /> `<AssemblyResolution>  <Directory Path>"D:\myfolder\bin\" includeSubDirectories="false"/> </AssemblyResolution>`|

## <a name="see-also"></a>Zobacz też
 [Dostosowywanie analizy pokrycia kodu](../test/customizing-code-coverage-analysis.md) [Określanie ustawień testu dla testów programu Visual Studio](https://msdn.microsoft.com/library/0c15317e-80c6-4317-aed3-82b8e15e3901)
