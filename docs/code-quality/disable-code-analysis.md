---
title: Wyłączanie analizy kodu
ms.date: 10/03/2019
ms.topic: conceptual
helpviewer_keywords:
- code analysis, disable
- disable code analysis
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 8db6ad7bed4b1526d87112f33d3586728728d7f5
ms.sourcegitcommit: 92361aac3665a934faa081e1d1ea89a067b01c5b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/17/2020
ms.locfileid: "79431400"
---
# <a name="how-to-disable-source-code-analysis-for-managed-code"></a>Jak wyłączyć analizę kodu źródłowego dla kodu zarządzanego

::: moniker range=">=vs-2019"

Ta strona pomaga wyłączyć analizę kodu w programie Visual Studio. Istnieją ograniczenia dotyczące tego, co można wyłączyć, a procedura wyłączania analizy kodu różni się w zależności od kilku czynników:

- Typ projektu (.NET Core/Standard a .NET Framework)

  Projekty .NET Core i .NET Standard mają opcje na stronie właściwości analizy kodu, które umożliwiają wyłączenie analizy kodu z analizatorów zainstalowanych jako pakiet NuGet. Aby uzyskać więcej informacji, zobacz [.NET Core i .NET Standard projects](#net-core-and-net-standard-projects). Aby wyłączyć analizę kodu źródłowego dla projektów programu .NET Framework, zobacz [projekty programu .NET Framework](#net-framework-projects).

- Analiza źródła a analiza starsza

  Ten temat dotyczy analizy kodu źródłowego, a nie do starszej analizy (binarnej). Aby uzyskać informacje dotyczące wyłączania starszej analizy, zobacz [Jak: Włączanie i wyłączanie starszej analizy kodu](how-to-enable-and-disable-automatic-code-analysis-for-managed-code.md).

## <a name="net-core-and-net-standard-projects"></a>Projekty .NET Core i .NET Standard

Począwszy od programu Visual Studio 2019 w wersji 16.3, istnieją dwa pola wyboru dostępne na stronie właściwości analizy kodu, które umożliwiają kontrolowanie, czy analizatory są uruchamiane w czasie kompilacji i czasie projektowania. Te opcje są specyficzne dla projektu.

![Włączanie lub wyłączanie analizy kodu na żywo lub kompilacji w programie Visual Studio](media/run-on-build-run-live-analysis.png)

Aby otworzyć tę stronę, kliknij prawym przyciskiem myszy węzeł projektu w **Eksploratorze rozwiązań** i wybierz polecenie **Właściwości**. Wybierz kartę **Analiza kodu.**

- Aby wyłączyć analizę źródła w czasie kompilacji, odznacz opcję **Uruchom na kompilacji.**
- Aby wyłączyć analizę źródeł na żywo, odznacz opcję **Uruchom na żywo analizy.**

> [!NOTE]
> Począwszy od programu Visual Studio 2019 w wersji 16.5, jeśli wolisz przepływ pracy wykonywania analizy kodu na żądanie, można wyłączyć wykonywanie analizatora podczas analizy na żywo i/lub kompilacji i ręcznie wyzwolić analizę kodu raz w projekcie lub rozwiązaniu na żądanie. Aby uzyskać informacje na temat ręcznego uruchamiania analizy kodu, zobacz [Jak: Ręcznie uruchamiać analizę kodu dla kodu zarządzanego](how-to-run-code-analysis-manually-for-managed-code.md).  

## <a name="net-framework-projects"></a>Projekty platformy .NET Framework

Aby wyłączyć analizę kodu źródłowego dla analizatorów, dodaj do [pliku projektu](../ide/solutions-and-projects-in-visual-studio.md#project-file)jedną lub więcej następujących właściwości MSBuild .

| Właściwość MSBuild | Opis | Domyślne |
| - | - | - |
| `RunAnalyzersDuringBuild` | Określa, czy analizatory są uruchamiane w czasie kompilacji. | `true` |
| `RunAnalyzersDuringLiveAnalysis` | Określa, czy analizatory analizują kod na żywo w czasie projektowania. | `true` |
| `RunAnalyzers` | Wyłącza analizatory w czasie kompilacji i projektowania. Ta właściwość ma `RunAnalyzersDuringBuild` `RunAnalyzersDuringLiveAnalysis`pierwszeństwo przed i . | `true` |

Przykłady:

```xml
<RunAnalyzersDuringBuild>false</RunAnalyzersDuringBuild>
<RunAnalyzersDuringLiveAnalysis>false</RunAnalyzersDuringLiveAnalysis>
<RunAnalyzers>false</RunAnalyzers>
```

::: moniker-end

::: moniker range="vs-2017"

## <a name="source-analysis"></a>Analiza źródła

Nie można wyłączyć [analizy źródłowej](roslyn-analyzers-overview.md) w programie Visual Studio 2017. Jeśli chcesz wyczyścić błędy analizatora z listy błędów, możesz pominąć wszystkie bieżące naruszenia, wybierając **pozycję Analizuj** > **analizę kodu przebiegu i Pomijaj aktywne problemy** na pasku menu. Aby uzyskać więcej informacji, zobacz [Pomijanie naruszeń](use-roslyn-analyzers.md#suppress-violations).

Począwszy od programu Visual Studio 2019 w wersji 16.3, można wyłączyć analizę kodu źródłowego lub wykonać go na żądanie. Należy rozważyć uaktualnienie do programu Visual Studio 2019.

## <a name="legacy-analysis"></a>Analiza w starszej wersji

Można wyłączyć starszą analizę czasu kompilacji na stronie właściwości **analizy kodu.** Aby uzyskać więcej informacji, zobacz [Jak: Włączanie i wyłączanie starszej analizy kodu](how-to-enable-and-disable-automatic-code-analysis-for-managed-code.md).

::: moniker-end

## <a name="see-also"></a>Zobacz też

- [Pomijanie naruszeń](use-roslyn-analyzers.md#suppress-violations)
- [Jak: Włączanie i wyłączanie starszej analizy kodu](how-to-enable-and-disable-automatic-code-analysis-for-managed-code.md)
