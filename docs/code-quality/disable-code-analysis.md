---
title: Wyłącz analizę kodu
ms.date: 10/03/2019
ms.topic: conceptual
helpviewer_keywords:
- code analysis, disable
- disable code analysis
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 77c189e4a15f2ae4049c45d2c8463079895f5be2
ms.sourcegitcommit: 39a04f42d23597b70053686d7e927ba78f38a9a8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/05/2019
ms.locfileid: "71975144"
---
# <a name="how-to-disable-source-code-analysis-for-managed-code"></a>Jak wyłączyć analizę kodu źródłowego dla kodu zarządzanego

::: moniker range=">=vs-2019"

Ta strona pomaga wyłączyć analizę kodu w programie Visual Studio. Istnieją ograniczenia dotyczące tego, co można wyłączyć, a procedura wyłączania analizy kodu różni się w zależności od kilku czynników:

- Typ projektu (.NET Core/Standard a .NET Framework)

  Projekty .NET Core i .NET Standard zawierają opcje na stronie właściwości analizy kodu, które umożliwiają wyłączenie analizy kodu z analizatorów zainstalowanych jako pakiet NuGet. Aby uzyskać więcej informacji, zobacz [.NET Core i .NET Standard projects](#net-core-and-net-standard-projects). Aby wyłączyć analizę kodu źródłowego dla projektów .NET Framework, zobacz [.NET Framework projects](#net-framework-projects).

- Pakiet narzędzia NuGet Analyzer a VSIX lub wbudowane analizatory

  Obecnie nie można wyłączyć analizy kodu na żywo dla wbudowanych analizatorów, na przykład identyfikator reguły IDE0067. Podobnie nie można wyłączyć analizy kodu na żywo dla analizatorów, które zostały zainstalowane w ramach rozszerzenia programu Visual Studio (VSIX). Aby pominąć błędy i ostrzeżenia z wbudowanych i opartych na VSIX analizatorów, wybierz **analizuj** > **kompilacja i Pomijaj aktywne problemy** na pasku menu. *Można* wyłączyć analizę na żywo i w czasie rzeczywistym dla analizatorów zainstalowanych w ramach pakietu NuGet.

- Analiza źródła a wersja do starszej analizy

  Ten temat ma zastosowanie do analizy kodu źródłowego, a nie do starszej wersji (binarnej) analizy. Aby uzyskać informacje na temat wyłączania starszej analizy, zobacz [How: Włącz i Wyłącz analizę starszego kodu @ no__t-0.

## <a name="net-core-and-net-standard-projects"></a>Projekty .NET Core i .NET Standard

Począwszy od programu Visual Studio 2019 w wersji 16,3, na stronie właściwości analizy kodu są dostępne dwa pola wyboru, które umożliwiają kontrolowanie, czy analizatory oparte na NuGet są uruchamiane w czasie kompilacji i w czasie projektowania. Te opcje są specyficzne dla projektu.

![Włącz lub Wyłącz analizę kodu na żywo lub po kompilacji w programie Visual Studio](media/run-on-build-run-live-analysis.png)

Aby otworzyć tę stronę, kliknij prawym przyciskiem myszy węzeł projektu w **Eksplorator rozwiązań** i wybierz polecenie **Właściwości**. Wybierz kartę **Analiza kodu** .

- Aby wyłączyć analizę źródła w czasie kompilacji, usuń zaznaczenie opcji **Uruchom przy kompilacji** .
- Aby wyłączyć analizę źródła na żywo, usuń zaznaczenie opcji **Uruchom przy użyciu analizy na żywo** .

> [!NOTE]
> Wbudowane i oparte na VSIX analizatory będą nadal zapewniać analizę na żywo kodu, nawet jeśli nie jest zaznaczone pole wyboru **Uruchom na żywo analizy** . Jeśli chcesz pominąć błędy i ostrzeżenia z tych analizatorów, wybierz pozycję **analizuj** > **kompilacja i Pomiń aktywne problemy** na pasku menu.

## <a name="net-framework-projects"></a>Projekty .NET Framework

Aby wyłączyć analizę kodu źródłowego dla analizatorów zainstalowanych w ramach pakietu NuGet, Dodaj co najmniej jedną z następujących właściwości programu MSBuild do [pliku projektu](../ide/solutions-and-projects-in-visual-studio.md#project-file).

| Właściwość programu MSBuild | Opis | Domyślny |
| - | - | - |
| `RunAnalyzersDuringBuild` | Określa, czy analizatory oparte na NuGet są uruchamiane w czasie kompilacji. | `true` |
| `RunAnalyzersDuringLiveAnalysis` | Określa, czy analizatory bazujące na NuGet analizują kod na żywo w czasie projektowania. | `true` |
| `RunAnalyzers` | Wyłącza analizatory oparte na NuGet w czasie kompilacji i projektowania. Ta właściwość ma pierwszeństwo przed `RunAnalyzersDuringBuild` i `RunAnalyzersDuringLiveAnalysis`. | `true` |

Przykłady:

```xml
<RunAnalyzersDuringBuild>false</RunAnalyzersDuringBuild>
<RunAnalyzersDuringLiveAnalysis>false</RunAnalyzersDuringLiveAnalysis>
<RunAnalyzers>false</RunAnalyzers>
```

::: moniker-end

::: moniker range="vs-2017"

## <a name="source-analysis"></a>Analiza źródła

Nie można wyłączyć [analizy źródła](roslyn-analyzers-overview.md) w programie Visual Studio 2017. Jeśli chcesz wyczyścić błędy analizatora z Lista błędów, możesz pominąć wszystkie bieżące naruszenia, wybierając pozycję **analizuj** > **Uruchom analizę kodu i pominąć aktywne problemy** na pasku menu. Aby uzyskać więcej informacji, zobacz [pomijanie naruszeń](use-roslyn-analyzers.md#suppress-violations).

Począwszy od programu Visual Studio 2019 w wersji 16,3, można wyłączyć analizę kodu źródłowego opartego na narzędziu NuGet. Rozważ uaktualnienie do programu Visual Studio 2019.

## <a name="legacy-analysis"></a>Analiza w starszej wersji

Starszą analizę czasu kompilacji można wyłączyć na stronie właściwości **analizy kodu** . Aby uzyskać więcej informacji, zobacz [jak: Włącz i Wyłącz analizę starszego kodu @ no__t-0.

::: moniker-end

## <a name="see-also"></a>Zobacz także

- [Pomiń naruszenia](use-roslyn-analyzers.md#suppress-violations)
- [Instrukcje: Włączanie i wyłączanie starszej wersji analizy kodu @ no__t-0