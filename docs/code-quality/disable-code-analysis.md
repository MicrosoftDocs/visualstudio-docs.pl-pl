---
title: Wyłącz analizę kodu
ms.date: 09/01/2020
description: Dowiedz się, jak wyłączyć analizę kodu źródłowego programu Visual Studio w projektach .NET Core, .NET Standard i .NET Framework.
ms.custom: SEO-VS-2020
ms.topic: how-to
helpviewer_keywords:
- code analysis, disable
- disable code analysis
author: mikadumont
ms.author: midumont
manager: jmartens
ms.openlocfilehash: 6a1f1466caa921d46ce4701f5074b98f3d5ba051
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99860389"
---
# <a name="disable-source-code-analysis-for-net"></a>Wyłącz analizę kodu źródłowego dla platformy .NET

::: moniker range=">=vs-2019"

Ta strona pomaga wyłączyć analizę kodu w programie Visual Studio. Istnieją ograniczenia dotyczące tego, co można wyłączyć, a procedura wyłączania analizy kodu różni się w zależności od kilku czynników:

- Typ projektu (.NET Core/Standard a .NET Framework)

  Projekty .NET Core i .NET Standard zawierają opcje na stronie właściwości analizy kodu, które umożliwiają wyłączenie analizy kodu z analizatorów zainstalowanych jako pakiet NuGet. Aby uzyskać więcej informacji, zobacz [.NET Core i .NET Standard projects](#net-core-and-net-standard-projects). Aby wyłączyć analizę kodu źródłowego dla projektów .NET Framework, zobacz [.NET Framework projects](#net-framework-projects).

- Analiza źródła a wersja do starszej analizy

  Ten temat ma zastosowanie do analizy kodu źródłowego, a nie do starszej wersji (binarnej) analizy. Aby uzyskać informacje na temat wyłączania starszej analizy, zobacz [How to: Enable and disable The Legacy Code Analysis](how-to-enable-and-disable-automatic-code-analysis-for-managed-code.md).

## <a name="net-core-and-net-standard-projects"></a>Projekty .NET Core i .NET Standard

Począwszy od programu Visual Studio 2019 w wersji 16,3, na stronie właściwości analizy kodu są dostępne dwa pola wyboru, które umożliwiają kontrolowanie, czy analizatory są uruchamiane w czasie kompilacji i w czasie projektowania. Te opcje są specyficzne dla projektu.

![Włącz lub Wyłącz analizę kodu na żywo lub po kompilacji w programie Visual Studio](media/run-on-build-run-live-analysis.png)

Aby otworzyć tę stronę, kliknij prawym przyciskiem myszy węzeł projektu w **Eksplorator rozwiązań** i wybierz polecenie **Właściwości**. Wybierz kartę **Analiza kodu** .

- Aby wyłączyć analizę źródła w czasie kompilacji, usuń zaznaczenie opcji **Uruchom przy kompilacji** .
- Aby wyłączyć analizę źródła na żywo, usuń zaznaczenie opcji **Uruchom przy użyciu analizy na żywo** .

> [!NOTE]
> Począwszy od programu Visual Studio 2019 w wersji 16,5, jeśli wolisz przepływ pracy do analizy kodu na żądanie, możesz wyłączyć wykonywanie analizatora podczas analizy na żywo i/lub skompilować i ręcznie wyzwolić analizę kodu w projekcie lub rozwiązaniu na żądanie. Aby uzyskać informacje na temat ręcznego uruchamiania analizy kodu, zobacz [How to: Run Code Analysis ręcznie dla kodu zarządzanego](how-to-run-code-analysis-manually-for-managed-code.md).

## <a name="net-framework-projects"></a>Projekty .NET Framework

Aby wyłączyć analizę kodu źródłowego dla analizatorów, Dodaj co najmniej jedną z następujących właściwości programu MSBuild do [pliku projektu](../ide/solutions-and-projects-in-visual-studio.md#project-file).

| Właściwość programu MSBuild | Opis | Domyślne |
| - | - | - |
| `RunAnalyzersDuringBuild` | Określa, czy analizatory są uruchamiane w czasie kompilacji. | `true` |
| `RunAnalyzersDuringLiveAnalysis` | Określa, czy analizatory analizują kod na żywo w czasie projektowania. | `true` |
| `RunAnalyzers` | Wyłącza analizatory w czasie kompilacji i projektowania. Ta właściwość ma pierwszeństwo przed `RunAnalyzersDuringBuild` i `RunAnalyzersDuringLiveAnalysis` . | `true` |

Przykłady:

```xml
<RunAnalyzersDuringBuild>false</RunAnalyzersDuringBuild>
<RunAnalyzersDuringLiveAnalysis>false</RunAnalyzersDuringLiveAnalysis>
<RunAnalyzers>false</RunAnalyzers>
```

::: moniker-end

::: moniker range="vs-2017"

## <a name="source-analysis"></a>Analiza źródła

Nie można wyłączyć [analizy źródła](roslyn-analyzers-overview.md) w programie Visual Studio 2017. Jeśli chcesz wyczyścić błędy analizatora z **Lista błędów**, możesz pominąć wszystkie bieżące naruszenia, wybierając **Analizuj**  >  **Run Code Analysis i pomijając aktywne problemy** na pasku menu. Aby uzyskać więcej informacji, zobacz [pomijanie naruszeń](use-roslyn-analyzers.md#suppress-violations).

Począwszy od programu Visual Studio 2019 w wersji 16,3, można wyłączyć analizę kodu źródłowego lub wykonać ją na żądanie. Rozważ uaktualnienie do programu Visual Studio 2019.

## <a name="legacy-analysis"></a>Analiza w starszej wersji

Starszą analizę czasu kompilacji można wyłączyć na stronie właściwości **analizy kodu** . Aby uzyskać więcej informacji, zobacz [How to: Enable and disable The Legacy Code Analysis](how-to-enable-and-disable-automatic-code-analysis-for-managed-code.md).

::: moniker-end

## <a name="see-also"></a>Zobacz też

- [Pomiń naruszenia](use-roslyn-analyzers.md#suppress-violations)
- [Instrukcje: Włączanie i wyłączanie analizy starszego kodu](how-to-enable-and-disable-automatic-code-analysis-for-managed-code.md)
