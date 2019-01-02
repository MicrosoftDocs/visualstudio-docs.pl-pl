---
title: Generowanie metryki kodu ze środowiskiem IDE lub wiersza polecenia
ms.date: 11/02/2018
ms.prod: visual-studio-dev15
ms.topic: conceptual
helpviewer_keywords:
- code metrics data
- code metrics results
- code metrics [Visual Studio]
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 96b74421d638a99823399a0049b712bc6c54c8a9
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/02/2019
ms.locfileid: "53849061"
---
# <a name="how-to-generate-code-metrics-data"></a>Instrukcje: Generowanie danych metryk kodu

Można wygenerować wyniki metryki kodu dla co najmniej jeden projekt lub całe rozwiązanie. Metryki kodu jest dostępna w środowisku opracowywanie interakcyjne (IDE) programu Visual Studio i dla C# i projektach języka Visual Basic, w wierszu polecenia.

Ponadto, możesz zainstalować [pakietu NuGet](https://dotnet.myget.org/feed/roslyn-analyzers/package/nuget/Microsoft.CodeAnalysis.FxCopAnalyzers/2.6.2-beta2-63202-01) zawierającego cztery metryki kodu [analizatora](roslyn-analyzers-overview.md) reguły: CA1501, CA1502, CA1505 i CA1506. Te reguły są domyślnie wyłączone, ale można je włączyć **Eksploratora rozwiązań** lub [zestaw reguł](using-rule-sets-to-group-code-analysis-rules.md) pliku.

## <a name="visual-studio-ide-code-metrics"></a>Metryki kodu w usłudze Visual Studio IDE

### <a name="generate-code-metrics-results-for-an-entire-solution"></a>Generowanie wyników metryk kodów dla całego rozwiązania

Wyniki metryki kodu dla całego rozwiązania można wygenerować w dowolnym z następujących sposobów:

- Na pasku menu wybierz **analizy** > **Oblicz metryki kodu** > **dla rozwiązania**.

- W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy rozwiązanie, a następnie wybierz **Oblicz metryki kodu**.

- W **wyników metryk kodów** oknie Wybierz **Oblicz metryki kodu dla rozwiązania** przycisku.

Wyniki są generowane i **wyników metryk kodów** zostanie wyświetlone okno. Aby wyświetlić szczegółowe wyniki wyszukiwania, rozwiń węzeł drzewa w **hierarchii** kolumny.

### <a name="generate-code-metrics-results-for-one-or-more-projects"></a>Generowanie wyników metryk kodów dla jednego lub więcej projektów

1. W **Eksploratora rozwiązań**, zaznacz jeden lub więcej projektów.

1. Na pasku menu wybierz **analizy** > **Oblicz metryki kodu** > **dla projektów wybrane**.

Wyniki są generowane i **wyników metryk kodów** zostanie wyświetlone okno. Aby wyświetlić szczegółowe wyniki wyszukiwania, rozwiń węzeł drzewa w **hierarchii**.

## <a name="command-line-code-metrics"></a>Metryki kodu wiersza polecenia

Można wygenerować danych metryk kodu z poziomu wiersza polecenia dla C# i projektach języka Visual Basic dla aplikacji .NET Framework, .NET Core i .NET Standard. Narzędzia wiersza polecenia metryki kodu jest wywoływana *Metrics.exe*.

Aby uzyskać *Metrics.exe* należy najpierw pliku wykonywalnego, [Generowanie samodzielnie](#generate-the-executable). W najbliższej przyszłości [opublikowanej wersji *Metrics.exe* będą dostępne](https://github.com/dotnet/roslyn-analyzers/issues/1756) więc nie trzeba tworzyć samodzielnie.

### <a name="generate-the-executable"></a>Generowanie pliku wykonywalnego

Aby wygenerować plik wykonywalny *Metrics.exe*, wykonaj następujące kroki:

1. Klonuj [analizatorów dotnet-roslyn](https://github.com/dotnet/roslyn-analyzers) repozytorium.
2. Otwórz wiersz polecenia programisty dla programu Visual Studio jako administrator.
3. Z folderu głównego **analizatorów roslyn** repozytorium, wykonaj następujące polecenie: `Restore.cmd`
4. Zmień katalog na *src\Tools*.
5. Wykonaj następujące polecenie, aby skompilować **Metrics.csproj** projektu:

   ```shell
   msbuild /m /v:m /p:Configuration=Release Metrics.csproj
   ```

   Plik wykonywalny o nazwie *Metrics.exe* jest generowany w *artifacts\bin* katalogu w katalogu głównym repozytorium.

   > [!TIP]
   > Tworzenie *Metrics.exe* w [ze starszej wersji trybu](#legacy-mode), wykonaj następujące polecenie:
   >
   > ```shell
   > msbuild /m /v:m /t:rebuild /p:LEGACY_CODE_METRICS_MODE=true Metrics.csproj
   > ```

### <a name="usage"></a>Użycie

Aby uruchomić *Metrics.exe*, podaj projekt lub rozwiązanie i dane wyjściowe XML pliku jako argumenty. Na przykład:

```shell
C:\>Metrics.exe /project:ConsoleApp20.csproj /out:report.xml
Loading ConsoleApp20.csproj...
Computing code metrics for ConsoleApp20.csproj...
Writing output to 'report.xml'...
Completed Successfully.
```

### <a name="output"></a>Dane wyjściowe

Wygenerowane dane wyjściowe XML ma następujący format:

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
                  <Method Name="void Program.Main(string[] args)" File="C:\Users\mavasani\source\repos\ConsoleApp20\ConsoleApp20\Program.cs" Line="7">
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

### <a name="tool-differences"></a>Narzędzie różnice

Poprzednie wersje programu Visual Studio, Visual Studio 2015, w tym uwzględnione narzędzie metryki kodu wiersza polecenia, o nazwie *Metrics.exe*. Ta wersja narzędzia zostało binarne analizy, oznacza to, na podstawie zestawu analiz. Nowe narzędzie analizuje kod źródłowy, zamiast tego. Ponieważ nowe *Metrics.exe* jest źródłem oparte na kodzie, wyniki są różne, co jest generowany przez poprzednie wersje programu *Metrics.exe* i w ramach programu Visual Studio 2017 IDE.

Nowy *Metrics.exe* narzędzia można obliczyć metryki, nawet w obecności błędy kodu źródłowego, tak długo, jak rozwiązania i projektu może być załadowany.

#### <a name="metric-value-differences"></a>Różnice wartość metryki

`LinesOfCode` Metryka jest bardziej dokładnych i wiarygodnych w nowym *Metrics.exe*. Jest niezależna od wszelkich różnic generowanie kodu i nie zmienia się podczas zmiany zestawu narzędzi lub środowiska uruchomieniowego. Nowy *Metrics.exe* liczby rzeczywiste wiersze kodu, w tym puste wiersze i komentarze.

Inne metryki, takie jak `CyclomaticComplexity` i `MaintainabilityIndex` używać tych samych formuł jako poprzednie wersje *Metrics.exe*, ale nowe *Metrics.exe* zlicza `IOperations` (logiczne źródła instrukcje) zamiast instrukcji języka pośredniego (IL). Numery będą nieco inne niż w poprzednich wersjach *Metrics.exe* i z wyników metryk kodów Visual Studio 2017 IDE.

### <a name="legacy-mode"></a>Starsza wersja trybu

Możesz również tworzyć *Metrics.exe* w *ze starszej wersji trybu*. Starsza wersja trybu wersję narzędzia generuje wartości metryk, znajdujących się bliżej jakie starsze wersje wygenerowany przez narzędzie. Ponadto w starszym trybie *Metrics.exe* generuje metryki kodu dla tego samego zestawu metody typów tego poprzednie wersje metryki kod wygenerowany przez narzędzie. Na przykład nie generować danych metryki kodu dla inicjatorów pola i właściwości. Starsza wersja trybu przydaje się wstecznej zgodności lub jeśli masz kod ewidencjonowania bramy na podstawie metryki kodu liczb. Polecenie, aby skompilować *Metrics.exe* w starszym trybie jest:

```shell
msbuild /m /v:m /t:rebuild /p:LEGACY_CODE_METRICS_MODE=true Metrics.csproj
```

Aby uzyskać więcej informacji, zobacz [Włącz generowanie metryki kodu w starszym trybie](https://github.com/dotnet/roslyn-analyzers/pull/1841).

## <a name="see-also"></a>Zobacz także

- [Korzystanie z okna wyników metryk kodów](../code-quality/working-with-code-metrics-data.md)
- [Wartości metryk kodów](../code-quality/code-metrics-values.md)
