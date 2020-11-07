---
title: Analiza kodu FxCop i analizatory FxCop
ms.date: 09/06/2018
description: Zapoznaj się z różnicą między starszymi analizatorami FxCop i FxCop w programie Visual Studio. Zobacz odpowiedzi na pytania dotyczące korzystania z tych analizatorów.
ms.custom: SEO-VS-2020
ms.topic: conceptual
helpviewer_keywords:
- code analysis FAQ
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 0e6768ad7f1ee87f75592c736b03bf6fd64e28c2
ms.sourcegitcommit: 75bfdaab9a8b23a097c1e8538ed1cde404305974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/07/2020
ms.locfileid: "94348961"
---
# <a name="frequently-asked-questions-about-fxcop-and-fxcop-analyzers"></a>Często zadawane pytania dotyczące analizatorów FxCop i FxCop

Zrozumienie różnic między starszymi analizatorami FxCop i FxCop może być nieco trudne. Ten artykuł ma na celu rozwiązanie niektórych pytań, które mogą wystąpić.

## <a name="whats-the-difference-between-legacy-fxcop-and-fxcop-analyzers"></a>Jaka jest różnica między starszymi analizatorami FxCop i FxCop?

Starsza FxCop uruchamia analizę po kompilacji dla skompilowanego zestawu. Działa jako oddzielny plik wykonywalny o nazwie **FxCopCmd.exe**. FxCopCmd.exe ładuje skompilowany zestaw, uruchamia analizę kodu, a następnie raportuje wyniki (lub *diagnostykę* ).

Analizatory FxCop są oparte na .NET Compiler Platform ("Roslyn"). Należy [je zainstalować jako pakiet NuGet](install-fxcop-analyzers.md#nuget-package) , do którego odwołuje się projekt lub rozwiązanie. Analizatory FxCop uruchamiają analizę opartą na kodzie źródłowym podczas wykonywania kompilatora. Analizatory FxCop są hostowane w ramach procesu kompilatora, **csc.exe** lub **vbc.exe** i uruchamiania analizy podczas kompilowania projektu. Wyniki analizatora są raportowane wraz z wynikami kompilatora.

> [!NOTE]
> Można także [zainstalować analizatory FxCop jako rozszerzenie programu Visual Studio](install-fxcop-analyzers.md#vsix). W takim przypadku analizatory są wykonywane podczas wpisywania w edytorze kodu, ale nie są wykonywane w czasie kompilacji. Jeśli chcesz uruchomić analizatory FxCop w ramach ciągłej integracji (CI), zamiast tego zainstaluj je jako pakiet NuGet.

## <a name="does-the-run-code-analysis-command-run-fxcop-analyzers"></a>Czy polecenie uruchomienia analizy kodu uruchamia analizatory FxCop?

Przed wydaniem programu Visual Studio 2019 16,5 w przypadku wybrania opcji **Analizuj**  >  **analizę kodu uruchamiania** zostanie wykonana Starsza analiza. Uruchamianie programu Visual Studio 2019 16,5, opcja **uruchamiania analizy kodu** wykonuje analizatory oparte na Roslyn dla wybranego projektu lub rozwiązania. Jeśli zainstalowano analizatory FxCop opartych na Roslyn, również zostaną one wykonane. Aby uzyskać więcej informacji, zobacz [jak: uruchamiać analizę kodu ręcznie dla kodu zarządzanego](how-to-run-code-analysis-manually-for-managed-code.md).

## <a name="does-the-runcodeanalysis-msbuild-project-property-run-analyzers"></a>Czy właściwość projektu MSBuild RunCodeAnalysis jest uruchamiana analizatory?

Nie. Właściwość **RunCodeAnalysis** w pliku projektu (na przykład *. csproj* ) jest używana tylko do wykonywania starszych FxCop. Uruchamia zadanie programu MSBuild po kompilacji, które wywołuje **FxCopCmd.exe**.

## <a name="so-how-do-i-run-fxcop-analyzers-then"></a>Jak uruchomić analizatory FxCop?

Aby uruchomić analizatory FxCop, najpierw [Zainstaluj dla nich pakiet NuGet](install-fxcop-analyzers.md) . Następnie Skompiluj projekt lub rozwiązanie z programu Visual Studio lub przy użyciu programu MSBuild. Ostrzeżenia i błędy generowane przez analizatory FxCop będą wyświetlane w **Lista błędów** lub w oknie wiersza polecenia.

## <a name="i-get-warning-ca0507-even-after-ive-installed-the-fxcop-analyzers-nuget-package"></a>Otrzymuję ostrzeżenie CA0507 nawet po zainstalowaniu pakietu NuGet analizatorów FxCop

Jeśli zainstalowano analizatory FxCop, ale nadal pojawia się ostrzeżenie CA0507 **"" Uruchomienie analizy kodu "zostało zaniechane na rzecz analizatorów FxCop, które są uruchamiane podczas kompilacji"** , może być konieczne ustawienie właściwości **RunCodeAnalysis** MSBuild w [pliku projektu](../ide/solutions-and-projects-in-visual-studio.md#project-file) na **false**. W przeciwnym razie Starsza analiza zostanie wykonana po każdej kompilacji.

```xml
<RunCodeAnalysis>false</RunCodeAnalysis>
```

## <a name="which-rules-have-been-ported-to-fxcop-analyzers"></a>Które reguły zostały przeanalizowane do analizatorów FxCop?

Aby uzyskać informacje o tym, które starsze reguły analizy zostały [przeanalizowane do analizatorów FxCop](install-fxcop-analyzers.md), zobacz [FxCop reguły stanu portu](fxcop-rule-port-status.md).

## <a name="code-analysis-warnings-are-treated-as-errors"></a>Ostrzeżenia analizy kodu są traktowane jako błędy

Jeśli projekt używa opcji kompilacja do traktowania ostrzeżeń jako błędów, ostrzeżenia analizatora FxCop mogą pojawić się jako błędy. Aby zapobiec potraktowaniu ostrzeżeń analizy kodu jako błędów, wykonaj kroki opisane w temacie [Analiza kodu — często zadawane pytania](../code-quality/analyzers-faq.md#treat-warnings-as-errors).

## <a name="see-also"></a>Zobacz też

- [Omówienie analizatorów .NET Compiler Platform](roslyn-analyzers-overview.md)
- [Migrowanie do analizatorów FxCop](migrate-from-legacy-analysis-to-fxcop-analyzers.md)
- [Instalowanie analizatorów FxCop](install-fxcop-analyzers.md)
