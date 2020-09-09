---
title: Generuj metryki kodu z poziomu środowiska IDE lub z wiersza polecenia
ms.date: 11/02/2018
ms.topic: how-to
helpviewer_keywords:
- code metrics data
- code metrics results
- code metrics [Visual Studio]
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 1b254cb2077b748f34958e33dbc456f17df530ce
ms.sourcegitcommit: ed4372bb6f4ae64f1fd712b2b253bf91d9ff96bf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/09/2020
ms.locfileid: "89600228"
---
# <a name="how-to-generate-code-metrics-data"></a>Instrukcje: generowanie danych metryk kodu

Dane metryk kodu można generować na trzy sposoby:

- Przez włączenie [analizatorów jakości kodu platformy .NET](#net-code-quality-analyzers-code-metrics-rules) i włączenie czterech reguł metryk kodu (łatwość konserwacji), które zawiera.

- Poprzez wybranie polecenia [ **Analizuj**  >  **metryki kodu** ](#calculate-code-metrics-menu-command) w programie Visual Studio.

- Z [wiersza polecenia](#command-line-code-metrics) dla projektów C# i Visual Basic.

## <a name="net-code-quality-analyzers-code-metrics-rules"></a>Reguły metryk kodu analizatorów jakości kodu platformy .NET

[Analizatory](roslyn-analyzers-overview.md) jakości kodu platformy .NET zawierają kilka reguł analizy metryk kodu:

- [CA1501](./ca1501.md)
- [CA1502](ca1502.md)
- [CA1505](ca1505.md)
- [CA1506](ca1506.md)

Te reguły są domyślnie wyłączone, ale można je włączyć z poziomu [**Eksplorator rozwiązań**](use-roslyn-analyzers.md#set-rule-severity-from-solution-explorer) lub w pliku [zestawu reguł](using-rule-sets-to-group-code-analysis-rules.md) . Na przykład, aby włączyć CA1502 reguły jako ostrzeżenie, plik zestawu reguł będzie zawierać następujący wpis:

```xml
<?xml version="1.0" encoding="utf-8"?>
<RuleSet Name="Rules" Description="Rules" ToolsVersion="16.0">
  <Rules AnalyzerId="Microsoft.CodeQuality.Analyzers" RuleNamespace="Microsoft.CodeQuality.Analyzers">
    <Rule Id="CA1502" Action="Warning" />
  </Rules>
</RuleSet>
```

### <a name="configuration"></a>Konfiguracja

Można skonfigurować progi, w których będą wyzwalane reguły metryki kodu.

1. Utwórz plik tekstowy. Na przykład możesz ją nazwać *CodeMetricsConfig.txt*.

2. Dodaj odpowiednie progi do pliku tekstowego w następującym formacie:

   ```txt
   CA1502: 10
   ```

   W tym przykładzie reguła [CA1502](ca1502.md) jest skonfigurowana do uruchamiania, gdy Złożoność cyklomatyczna metody jest większa niż 10.

3. W oknie **Właściwości** programu Visual Studio lub w pliku projektu Oznacz akcję kompilacja pliku konfiguracji jako [**AdditionalFiles**](../ide/build-actions.md#build-action-values). Przykład:

   ```xml
   <ItemGroup>
     <AdditionalFiles Include="CodeMetricsConfig.txt" />
   </ItemGroup>
   ```

## <a name="calculate-code-metrics-menu-command"></a>Polecenie Oblicz metryki kodu — menu

Generuj metryki kodu dla jednego lub wszystkich otwartych projektów w środowisku IDE przy użyciu menu **Analizuj**  >  **metryki kodu** .

### <a name="generate-code-metrics-results-for-an-entire-solution"></a>Generuj wyniki metryk kodu dla całego rozwiązania

Można generować wyniki metryk kodu dla całego rozwiązania w dowolny z następujących sposobów:

- Na pasku menu wybierz pozycję **Analizuj**  >  **Oblicz metryki kodu**  >  **dla rozwiązania**.

- W **Eksplorator rozwiązań**kliknij prawym przyciskiem myszy rozwiązanie, a następnie wybierz polecenie **Oblicz metryki kodu**.

- W oknie **wyników metryk kodu** wybierz przycisk **Oblicz metryki kodu dla rozwiązania** .

Wyniki są generowane i zostanie wyświetlone okno **wyników metryk kodu** . Aby wyświetlić szczegóły wyników, rozwiń drzewo w kolumnie **Hierarchia** .

### <a name="generate-code-metrics-results-for-one-or-more-projects"></a>Generuj wyniki metryk kodu dla jednego lub wielu projektów

1. W **Eksplorator rozwiązań**wybierz co najmniej jeden projekt.

1. Na pasku menu wybierz pozycję **Analizuj**  >  **Oblicz metryki kodu**  >  **dla wybranych projektów**.

Wyniki są generowane i zostanie wyświetlone okno **wyników metryk kodu** . Aby wyświetlić szczegóły wyników, rozwiń drzewo w **hierarchii**.

::: moniker range="vs-2017"

> [!NOTE]
> Polecenie **Oblicz metryki kodu** nie działa w przypadku projektów .NET Core i .NET Standard. Aby obliczyć metryki kodu dla projektu .NET Core lub .NET Standard, można:
>
> - Zamiast tego Oblicz metrykę kodu z poziomu [wiersza polecenia](#command-line-code-metrics)
>
> - Uaktualnianie do [programu Visual Studio 2019](https://visualstudio.microsoft.com/downloads)

::: moniker-end

## <a name="command-line-code-metrics"></a>Metryki kodu wiersza polecenia

Można generować dane metryk kodu z wiersza polecenia dla projektów C# i Visual Basic dla aplikacji .NET Framework, .NET Core i .NET Standard. Aby uruchomić metryki kodu z wiersza polecenia, należy zainstalować [pakiet NuGet Microsoft. CodeAnalysis. Metrics](#microsoftcodeanalysismetrics-nuget-package) lub skompilować samodzielnie plik wykonywalny [Metrics.exe](#metricsexe) .

### <a name="microsoftcodeanalysismetrics-nuget-package"></a>Pakiet NuGet Microsoft. CodeAnalysis. Metrics

Najprostszym sposobem generowania danych metryk kodu z wiersza polecenia jest zainstalowanie pakietu NuGet [Microsoft. CodeAnalysis. Metrics](https://www.nuget.org/packages/Microsoft.CodeAnalysis.Metrics/) . Po zainstalowaniu pakietu Uruchom polecenie `msbuild /t:Metrics` z katalogu, który zawiera plik projektu. Przykład:

```shell
C:\source\repos\ClassLibrary3\ClassLibrary3>msbuild /t:Metrics
Microsoft (R) Build Engine version 16.0.360-preview+g9781d96883 for .NET Framework
Copyright (C) Microsoft Corporation. All rights reserved.

Build started 1/22/2019 4:29:57 PM.
Project "C:\source\repos\ClassLibrary3\ClassLibrary3\ClassLibrary3.csproj" on node 1 (Metrics target(s))
.
Metrics:
  C:\source\repos\ClassLibrary3\packages\Microsoft.CodeMetrics.2.6.4-ci\build\\..\Metrics\Metrics.exe /project:C:\source\repos\ClassLibrary3\ClassLibrary3\ClassLibrary3.csproj /out:ClassLibrary3.Metrics.xml
  Loading ClassLibrary3.csproj...
  Computing code metrics for ClassLibrary3.csproj...
  Writing output to 'ClassLibrary3.Metrics.xml'...
  Completed Successfully.
Done Building Project "C:\source\repos\ClassLibrary3\ClassLibrary3\ClassLibrary3.csproj" (Metrics target(s)).

Build succeeded.
    0 Warning(s)
    0 Error(s)
```

Można zastąpić nazwę pliku wyjściowego, określając `/p:MetricsOutputFile=<filename>` . Możesz również uzyskać dane metryk kodu w [starszej wersji](#previous-versions) , określając `/p:LEGACY_CODE_METRICS_MODE=true` . Przykład:

```shell
C:\source\repos\ClassLibrary3\ClassLibrary3>msbuild /t:Metrics /p:LEGACY_CODE_METRICS_MODE=true /p:MetricsOutputFile="Legacy.xml"
Microsoft (R) Build Engine version 16.0.360-preview+g9781d96883 for .NET Framework
Copyright (C) Microsoft Corporation. All rights reserved.

Build started 1/22/2019 4:31:00 PM.
The "MetricsOutputFile" property is a global property, and cannot be modified.
Project "C:\source\repos\ClassLibrary3\ClassLibrary3\ClassLibrary3.csproj" on node 1 (Metrics target(s))
.
Metrics:
  C:\source\repos\ClassLibrary3\packages\Microsoft.CodeMetrics.2.6.4-ci\build\\..\Metrics.Legacy\Metrics.Legacy.exe /project:C:\source\repos\ClassLibrary3\ClassLibrary3\ClassLibrary3.csproj /out:Legacy.xml
  Loading ClassLibrary3.csproj...
  Computing code metrics for ClassLibrary3.csproj...
  Writing output to 'Legacy.xml'...
  Completed Successfully.
Done Building Project "C:\source\repos\ClassLibrary3\ClassLibrary3\ClassLibrary3.csproj" (Metrics target(s)).

Build succeeded.
    0 Warning(s)
    0 Error(s)
```

### <a name="code-metrics-output"></a>Dane wyjściowe metryk kodu

Wygenerowane dane wyjściowe XML mają następujący format:

::: moniker range=">=vs-2019"

```xml
<?xml version="1.0" encoding="utf-8"?>
<CodeMetricsReport Version="1.0">
  <Targets>
    <Target Name="ConsoleApp20.csproj">
      <Assembly Name="ConsoleApp20, Version=1.0.0.0, Culture=neutral, PublicKeyToken=null">
        <Metrics>
          <Metric Name="MaintainabilityIndex" Value="100" />
          <Metric Name="CyclomaticComplexity" Value="1" />
          <Metric Name="ClassCoupling" Value="1" />
          <Metric Name="DepthOfInheritance" Value="1" />
          <Metric Name="SourceLines" Value="11" />
          <Metric Name="ExecutableLines" Value="1" />
        </Metrics>
        <Namespaces>
          <Namespace Name="ConsoleApp20">
            <Metrics>
              <Metric Name="MaintainabilityIndex" Value="100" />
              <Metric Name="CyclomaticComplexity" Value="1" />
              <Metric Name="ClassCoupling" Value="1" />
              <Metric Name="DepthOfInheritance" Value="1" />
              <Metric Name="SourceLines" Value="11" />
              <Metric Name="ExecutableLines" Value="1" />
            </Metrics>
            <Types>
              <NamedType Name="Program">
                <Metrics>
                  <Metric Name="MaintainabilityIndex" Value="100" />
                  <Metric Name="CyclomaticComplexity" Value="1" />
                  <Metric Name="ClassCoupling" Value="1" />
                  <Metric Name="DepthOfInheritance" Value="1" />
                  <Metric Name="SourceLines" Value="7" />
                  <Metric Name="ExecutableLines" Value="1" />
                </Metrics>
                <Members>
                  <Method Name="void Program.Main(string[] args)" File="C:\source\repos\ConsoleApp20\ConsoleApp20\Program.cs" Line="7">
                    <Metrics>
                      <Metric Name="MaintainabilityIndex" Value="100" />
                      <Metric Name="CyclomaticComplexity" Value="1" />
                      <Metric Name="ClassCoupling" Value="1" />
                      <Metric Name="SourceLines" Value="4" />
                      <Metric Name="ExecutableLines" Value="1" />
                    </Metrics>
                  </Method>
                </Members>
              </NamedType>
            </Types>
          </Namespace>
        </Namespaces>
      </Assembly>
    </Target>
  </Targets>
</CodeMetricsReport>
```

::: moniker-end
::: moniker range="vs-2017"

```xml
<?xml version="1.0" encoding="utf-8"?>
<CodeMetricsReport Version="1.0">
  <Targets>
    <Target Name="ConsoleApp20.csproj">
      <Assembly Name="ConsoleApp20, Version=1.0.0.0, Culture=neutral, PublicKeyToken=null">
        <Metrics>
          <Metric Name="MaintainabilityIndex" Value="100" />
          <Metric Name="CyclomaticComplexity" Value="1" />
          <Metric Name="ClassCoupling" Value="1" />
          <Metric Name="DepthOfInheritance" Value="1" />
          <Metric Name="LinesOfCode" Value="11" />
        </Metrics>
        <Namespaces>
          <Namespace Name="ConsoleApp20">
            <Metrics>
              <Metric Name="MaintainabilityIndex" Value="100" />
              <Metric Name="CyclomaticComplexity" Value="1" />
              <Metric Name="ClassCoupling" Value="1" />
              <Metric Name="DepthOfInheritance" Value="1" />
              <Metric Name="LinesOfCode" Value="11" />
            </Metrics>
            <Types>
              <NamedType Name="Program">
                <Metrics>
                  <Metric Name="MaintainabilityIndex" Value="100" />
                  <Metric Name="CyclomaticComplexity" Value="1" />
                  <Metric Name="ClassCoupling" Value="1" />
                  <Metric Name="DepthOfInheritance" Value="1" />
                  <Metric Name="LinesOfCode" Value="7" />
                </Metrics>
                <Members>
                  <Method Name="void Program.Main(string[] args)" File="C:\source\repos\ConsoleApp20\ConsoleApp20\Program.cs" Line="7">
                    <Metrics>
                      <Metric Name="MaintainabilityIndex" Value="100" />
                      <Metric Name="CyclomaticComplexity" Value="1" />
                      <Metric Name="ClassCoupling" Value="1" />
                      <Metric Name="LinesOfCode" Value="4" />
                    </Metrics>
                  </Method>
                </Members>
              </NamedType>
            </Types>
          </Namespace>
        </Namespaces>
      </Assembly>
    </Target>
  </Targets>
</CodeMetricsReport>
```

::: moniker-end

### <a name="metricsexe"></a>Metrics.exe

Jeśli nie chcesz instalować pakietu NuGet, możesz bezpośrednio wygenerować *Metrics.exe* plik wykonywalny i użyć go. Aby wygenerować *Metrics.exe* pliku wykonywalnego:

1. Sklonuj repozytorium [dotnet/Roslyn-analizatory](https://github.com/dotnet/roslyn-analyzers) .
2. Otwórz wiersz polecenia dla deweloperów dla programu Visual Studio jako administrator.
3. Z poziomu katalogu głównego repozytorium **Roslyn-analizators** wykonaj następujące polecenie: `Restore.cmd`
4. Zmień katalog na *src\Tools*.
5. Wykonaj następujące polecenie, aby skompilować projekt **Metrics. csproj** :

   ```shell
   msbuild /m /v:m /p:Configuration=Release Metrics.csproj
   ```

   Plik wykonywalny o nazwie *Metrics.exe* jest generowany w katalogu *artifacts\bin* w obszarze głównym repozytorium.

#### <a name="metricsexe-usage"></a>Użycie Metrics.exe

Aby uruchomić *Metrics.exe*, podaj projekt lub rozwiązanie oraz wyjściowy plik XML jako argumenty. Przykład:

```shell
C:\>Metrics.exe /project:ConsoleApp20.csproj /out:report.xml
Loading ConsoleApp20.csproj...
Computing code metrics for ConsoleApp20.csproj...
Writing output to 'report.xml'...
Completed Successfully.
```

#### <a name="legacy-mode"></a>Tryb starszej wersji

Możesz wybrać kompilację *Metrics.exe* w *trybie starszej wersji*. Wersja w trybie starszej wersji narzędzia generuje wartości metryk, które są bliższe tym, które [starsze wersje narzędzia zostały wygenerowane](#previous-versions). Ponadto w trybie starszej *Metrics.exe* generuje metryki kodu dla tego samego zestawu typów metod, które są generowane przez poprzednie wersje narzędzia. Na przykład nie generuje danych metryk kodu dla inicjatorów pola i właściwości. Starszy tryb jest przydatny do zapewnienia zgodności z poprzednimi wersjami lub jeśli masz bramy ewidencjonowania kodu na podstawie numerów metryk kodu. Polecenie do kompilowania *Metrics.exe* w trybie starszej wersji:

```shell
msbuild /m /v:m /t:rebuild /p:LEGACY_CODE_METRICS_MODE=true Metrics.csproj
```

Aby uzyskać więcej informacji, zobacz [Włączanie generowania metryk kodu w trybie starszej wersji](https://github.com/dotnet/roslyn-analyzers/pull/1841).

### <a name="previous-versions"></a>Poprzednie wersje

::: moniker range=">=vs-2019"
Program Visual Studio 2015 zawiera narzędzie metryk kodu wiersza polecenia, które było również nazywane *Metrics.exe*. Ta Poprzednia wersja narzędzia wykonała analizę binarną, czyli analizę opartą na zestawie. Nowsza wersja narzędzia *Metrics.exe* analizuje zamiast niego kod źródłowy. Ponieważ nowszy *Metrics.exe* narzędzie jest oparte na kodzie źródłowym, wyniki metryk kodu wiersza polecenia mogą różnić się od tych generowanych przez środowisko IDE programu Visual Studio i poprzednie wersje *Metrics.exe*. Począwszy od programu Visual Studio 2019, środowisko IDE programu Visual Studio analizuje kod źródłowy, taki jak narzędzie wiersza polecenia, a wyniki powinny być takie same.

::: moniker-end
::: moniker range="vs-2017"
Program Visual Studio 2015 zawiera narzędzie metryk kodu wiersza polecenia, które było również nazywane *Metrics.exe*. Ta Poprzednia wersja narzędzia wykonała analizę binarną, czyli analizę opartą na zestawie. Nowe narzędzie *Metrics.exe* analizuje zamiast niego kod źródłowy. Ponieważ nowe narzędzie *Metrics.exe* jest oparte na kodzie źródłowym, wyniki metryk kodu wiersza polecenia są inne niż te wygenerowane przez środowisko IDE programu Visual Studio i poprzednie wersje *Metrics.exe*.
::: moniker-end

Nowe narzędzie metryk kodu wiersza polecenia oblicza metryki nawet w obecności błędów kodu źródłowego, o ile można załadować rozwiązanie i projekt.

#### <a name="metric-value-differences"></a>Różnice wartości metryk

::: moniker range=">=vs-2019"
Począwszy od programu Visual Studio 2019 w wersji 16,4 i Microsoft. CodeAnalysis. metics (2.9.5) `SourceLines` i `ExecutableLines` Zastąp poprzednią `LinesOfCode` metrykę. Aby uzyskać opisy nowych metryk, zobacz [wartości metryki kodu](../code-quality/code-metrics-values.md). Ta `LinesOfCode` Metryka jest dostępna w trybie starszej wersji.
::: moniker-end
::: moniker range="vs-2017"
`LinesOfCode`Metryka jest bardziej dokładna i niezawodna w nowym narzędziu metryk kodu wiersza polecenia. Jest on niezależny od jakichkolwiek różnic codegen i nie ulega zmianie, gdy zmieni się zestaw narzędzi lub środowisko uruchomieniowe. Nowe narzędzie zlicza rzeczywiste wiersze kodu, w tym puste wiersze i komentarze.
::: moniker-end

Inne metryki, takie jak `CyclomaticComplexity` i `MaintainabilityIndex` używają tych samych formuł co poprzednie wersje *Metrics.exe*, ale nowe narzędzie zlicza liczbę `IOperations` (instrukcje logicznego źródła) zamiast instrukcji języka pośredniego (IL). Liczby będą nieco inne niż te, które są generowane przez środowisko IDE programu Visual Studio i poprzednie wersje *Metrics.exe*.

## <a name="see-also"></a>Zobacz też

- [Korzystanie z okna wyników metryk kodu](../code-quality/working-with-code-metrics-data.md)
- [Wartości metryk kodu](../code-quality/code-metrics-values.md)