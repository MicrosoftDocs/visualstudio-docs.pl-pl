---
title: Generowanie metryk kodu z ide lub wiersza polecenia
ms.date: 11/02/2018
ms.topic: conceptual
helpviewer_keywords:
- code metrics data
- code metrics results
- code metrics [Visual Studio]
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 1abae26ed8a5e5db74f7b0d04db66d9d99930d5c
ms.sourcegitcommit: ade07bd1cf69b8b494d171ae648cfdd54f7800d3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/21/2020
ms.locfileid: "81649315"
---
# <a name="how-to-generate-code-metrics-data"></a>Jak: Generowanie danych metryk kodu

Dane dotyczące kodu można wygenerować na trzy sposoby:

- Instalując [analizatory FxCop](#fxcop-analyzers-code-metrics-rules) i włączając cztery reguły metryk kodu (możliwość konserwacji), które zawiera.

- Wybierając polecenie menu [ **Analizuj** > obliczanie metryk kodu](#calculate-code-metrics-menu-command) w programie Visual Studio.

- Z [wiersza polecenia](#command-line-code-metrics) dla projektów C# i Visual Basic.

## <a name="fxcop-analyzers-code-metrics-rules"></a>Reguły metryk kodu analizatorów FxCop

[Pakiet FxCopAnalyzers NuGet](https://www.nuget.org/packages/Microsoft.CodeAnalysis.FxCopAnalyzers) zawiera kilka reguł [analizatora](roslyn-analyzers-overview.md) metryk kodu:

- [CA1501](ca1501-avoid-excessive-inheritance.md)
- [CA1502](ca1502.md)
- [1505 urząd certyfikacji](ca1505.md)
- [CA1506](ca1506.md)

Reguły te są domyślnie wyłączone, ale można je włączyć w [**Eksploratorze rozwiązań**](use-roslyn-analyzers.md#set-rule-severity-from-solution-explorer) lub w pliku [zestawu reguł.](using-rule-sets-to-group-code-analysis-rules.md) Na przykład, aby włączyć regułę CA1502 jako ostrzeżenie, plik .ruleet będzie zawierał następujący wpis:

```xml
<?xml version="1.0" encoding="utf-8"?>
<RuleSet Name="Rules" Description="Rules" ToolsVersion="16.0">
  <Rules AnalyzerId="Microsoft.CodeQuality.Analyzers" RuleNamespace="Microsoft.CodeQuality.Analyzers">
    <Rule Id="CA1502" Action="Warning" />
  </Rules>
</RuleSet>
```

### <a name="configuration"></a>Konfigurowanie

Można skonfigurować progi, w których reguły metryki kodu w analizatorach FxCop pakiet ognia.

1. Tworzenie pliku tekstowego. Na przykład można nazwać go *CodeMetricsConfig.txt*.

2. Dodaj żądane progi do pliku tekstowego w następującym formacie:

   ```txt
   CA1502: 10
   ```

   W tym przykładzie reguła [CA1502](ca1502.md) jest skonfigurowana do ognia, gdy złożoność cyklomatyczna metody jest większa niż 10.

3. W oknie **Właściwości** programu Visual Studio lub w pliku projektu oznacz akcję kompilacji pliku konfiguracyjnego jako [**AdditionalFiles**](../ide/build-actions.md#build-action-values). Przykład:

   ```xml
   <ItemGroup>
     <AdditionalFiles Include="CodeMetricsConfig.txt" />
   </ItemGroup>
   ```

## <a name="calculate-code-metrics-menu-command"></a>Polecenie menu Oblicz metryki kodu

Generowanie metryk kodu dla jednego lub wszystkich otwartych projektów w IDE przy użyciu **analizy** > **obliczanie metryk kodu** menu.

### <a name="generate-code-metrics-results-for-an-entire-solution"></a>Generowanie wyników metryk kodu dla całego rozwiązania

Wyniki metryk kodu dla całego rozwiązania można wygenerować w dowolny z następujących sposobów:

- Na pasku menu wybierz pozycję >  **Analizuj** > **obliczanie metryk kodu**dla**rozwiązania**.

- W **Eksploratorze rozwiązań**kliknij prawym przyciskiem myszy rozwiązanie, a następnie wybierz polecenie **Oblicz metryki kodu**.

- W oknie **Wyniki metryk kodu** wybierz przycisk **Oblicz metryki kodu dla rozwiązania.**

Wyniki są generowane i zostanie wyświetlone okno **Wyniki metryk kodu.** Aby wyświetlić szczegóły wyników, rozwiń drzewo w kolumnie **Hierarchia.**

### <a name="generate-code-metrics-results-for-one-or-more-projects"></a>Generowanie wyników metryk kodu dla jednego lub większej liczby projektów

1. W **Eksploratorze rozwiązań**wybierz jeden lub więcej projektów.

1. Na pasku menu wybierz pozycję **Analizuj** > **metryki** > obliczania kodu dla wybranych**projektów.**

Wyniki są generowane i zostanie wyświetlone okno **Wyniki metryk kodu.** Aby wyświetlić szczegóły wyników, rozwiń drzewo w **hierarchii**.

::: moniker range="vs-2017"

> [!NOTE]
> Polecenie **Oblicz metryki kodu** nie działa w przypadku projektów .NET Core i .NET Standard. Aby obliczyć metryki kodu dla projektu .NET Core lub .NET Standard, można:
>
> - Obliczanie danych kodu z [wiersza polecenia](#command-line-code-metrics) zamiast tego
>
> - Uaktualnienie do [programu Visual Studio 2019](https://visualstudio.microsoft.com/downloads)

::: moniker-end

## <a name="command-line-code-metrics"></a>Metryki kodu wiersza polecenia

Można wygenerować dane metryk kodu z wiersza polecenia dla projektów języka C# i Visual Basic dla aplikacji .NET Framework, .NET Core i .NET Standard. Aby uruchomić metryki kodu z wiersza polecenia, zainstaluj [pakiet Microsoft.CodeAnalysis.Metrics NuGet](#microsoftcodeanalysismetrics-nuget-package) lub skompiluj plik wykonywalny [Metrics.exe](#metricsexe) samodzielnie.

### <a name="microsoftcodeanalysismetrics-nuget-package"></a>Pakiet Microsoft.CodeAnalysis.Metrics NuGet

Najprostszym sposobem generowania danych metryk kodu z wiersza polecenia jest zainstalowanie pakietu [Microsoft.CodeAnalysis.Metrics](https://www.nuget.org/packages/Microsoft.CodeAnalysis.Metrics/) NuGet. Po zainstalowaniu pakietu uruchom `msbuild /t:Metrics` z katalogu zawierającego plik projektu. Przykład:

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

Nazwę pliku wyjściowego można zastąpić, `/p:MetricsOutputFile=<filename>`określając program . Można również uzyskać dane metryk kodu [starszego stylu,](#previous-versions) określając `/p:LEGACY_CODE_METRICS_MODE=true`. Przykład:

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

### <a name="metricsexe"></a>Plik Metrics.exe

Jeśli nie chcesz instalować pakietu NuGet, możesz bezpośrednio wygenerować i użyć pliku wykonywalnego *Metrics.exe.* Aby wygenerować plik wykonywalny *Metrics.exe:*

1. Sklonuj [repozytorium dotnet/roslyn-analyzers.](https://github.com/dotnet/roslyn-analyzers)
2. Otwórz wiersz polecenia dewelopera dla programu Visual Studio jako administrator.
3. Z katalogu głównego **repozytora analizatorów roslyn** wykonaj następujące polecenie:`Restore.cmd`
4. Zmień katalog na *src\Tools*.
5. Wykonaj następujące polecenie, aby utworzyć projekt **Metrics.csproj:**

   ```shell
   msbuild /m /v:m /p:Configuration=Release Metrics.csproj
   ```

   Plik wykonywalny o nazwie *Metrics.exe* jest generowany w katalogu *artifacts\bin* w katalogu repozytorium repozytorium.

#### <a name="metricsexe-usage"></a>Użycie pliku Metrics.exe

Aby uruchomić *program Metrics.exe,* należy podać projekt lub rozwiązanie oraz wyjściowy plik XML jako argumenty. Przykład:

```shell
C:\>Metrics.exe /project:ConsoleApp20.csproj /out:report.xml
Loading ConsoleApp20.csproj...
Computing code metrics for ConsoleApp20.csproj...
Writing output to 'report.xml'...
Completed Successfully.
```

#### <a name="legacy-mode"></a>Tryb starszej wersji

Można utworzyć *metrics.exe* w *trybie starszej wersji*. Starsza wersja trybu narzędzia generuje wartości metryki, które są bliższe [starszej wersji narzędzia generowane.](#previous-versions) Ponadto w trybie starszej wersji *Metrics.exe* generuje metryki kodu dla tego samego zestawu typów metod, które poprzednie wersje narzędzia generowane metryki kodu dla. Na przykład nie generuje danych metryk kodu dla inicjatorów pól i właściwości. Starszy tryb jest przydatny w przypadku zgodności z powrotem lub jeśli masz bramy ewidencjonowania kodu na podstawie numerów metryk kodu. Polecenie do tworzenia *pliku Metrics.exe* w trybie starszej wersji jest następujące:

```shell
msbuild /m /v:m /t:rebuild /p:LEGACY_CODE_METRICS_MODE=true Metrics.csproj
```

Aby uzyskać więcej informacji, zobacz [Włączanie generowania metryk kodu w trybie starszej wersji .](https://github.com/dotnet/roslyn-analyzers/pull/1841)

### <a name="previous-versions"></a>Poprzednie wersje

::: moniker range=">=vs-2019"
Program Visual Studio 2015 zawierał narzędzie metryk kodu wiersza polecenia, które było również nazywane *Metrics.exe*. Ta poprzednia wersja narzędzia wykonała analizę binarną, czyli analizę opartą na zestawie. Nowsza wersja narzędzia *Metrics.exe* analizuje zamiast tego kod źródłowy. Ponieważ *nowsze narzędzie Metrics.exe* jest oparte na kodzie źródłowym, wyniki metryk kodu wiersza polecenia mogą różnić się od wyników generowanych przez ide programu Visual Studio i przez poprzednie wersje *programu Metrics.exe*. Począwszy od programu Visual Studio 2019, Visual Studio IDE analizuje kod źródłowy, takich jak narzędzie wiersza polecenia i wyniki powinny być takie same.

::: moniker-end
::: moniker range="vs-2017"
Program Visual Studio 2015 zawierał narzędzie metryk kodu wiersza polecenia, które było również nazywane *Metrics.exe*. Ta poprzednia wersja narzędzia wykonała analizę binarną, czyli analizę opartą na zestawie. Nowe narzędzie *Metrics.exe* analizuje zamiast tego kod źródłowy. Ponieważ nowe narzędzie *Metrics.exe* jest oparte na kodzie źródłowym, wyniki metryk kodu wiersza polecenia różnią się od wyników generowanych przez ide programu Visual Studio i przez poprzednie wersje *programu Metrics.exe*.
::: moniker-end

Nowe narzędzie metryk kodu wiersza polecenia oblicza metryki nawet w obecności błędów kodu źródłowego, o ile można załadować rozwiązanie i projekt.

#### <a name="metric-value-differences"></a>Różnice wartości metryki

::: moniker range=">=vs-2019"
Począwszy od programu Visual Studio 2019 w wersji 16.4 i Microsoft.CodeAnalysis.Metics (2.9.5) `SourceLines` i `ExecutableLines` zastąpić poprzednią `LinesOfCode` metrykę. Aby uzyskać opisy nowych danych, zobacz [Kod wartości metryk](../code-quality/code-metrics-values.md). Metryka `LinesOfCode` jest dostępna w trybie starszej wersji.
::: moniker-end
::: moniker range="vs-2017"
Metryka jest dokładniejsza `LinesOfCode` i bardziej niezawodna w nowym narzędziu metryk kodu wiersza polecenia. Jest niezależna od różnic codegen i nie zmienia się, gdy zmienia się zestaw narzędzi lub środowisko uruchomieniowe. Nowe narzędzie zlicza rzeczywiste wiersze kodu, w tym puste wiersze i komentarze.
::: moniker-end

Inne metryki, `CyclomaticComplexity` `MaintainabilityIndex` takie jak i używają tych samych formuł, co poprzednie wersje *programu Metrics.exe,* ale nowe narzędzie zlicza instrukcje `IOperations` (instrukcje źródła logicznego) zamiast instrukcji języka pośredniego (IL). Liczby będą nieco inne niż te generowane przez ide programu Visual Studio i przez poprzednie wersje *programu Metrics.exe*.

## <a name="see-also"></a>Zobacz też

- [Użyj okna Wyniki metryk kodu](../code-quality/working-with-code-metrics-data.md)
- [Wartości metryk kodu](../code-quality/code-metrics-values.md)
