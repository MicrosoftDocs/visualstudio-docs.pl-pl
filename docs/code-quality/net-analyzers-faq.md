---
title: Analiza kodu FxCop (analiza binarna) i analizatory .NET (analiza źródła)
ms.date: 09/06/2018
description: Zapoznaj się z różnicą między starszą FxCop (analizą binarną) i analizatorami .NET (analiza źródła) w programie Visual Studio. Zobacz odpowiedzi na pytania dotyczące korzystania z tych analizatorów.
ms.custom: SEO-VS-2020
ms.topic: conceptual
helpviewer_keywords:
- code analysis FAQ
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: d581ef60ebfe9ff5aeceae4c16ee4294eae5d850
ms.sourcegitcommit: 967c2f8c1b3f805cf42c0246389517689d971b53
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/25/2020
ms.locfileid: "96112247"
---
# <a name="frequently-asked-questions-about-legacy-fxcop-and-net-analyzers"></a>Często zadawane pytania dotyczące starszych analizatorów FxCop i .NET

Zrozumienie różnic między starszym FxCop (analizą binarną) i analizatorami .NET (analiza źródła) może być nieco trudne. Ten artykuł ma na celu rozwiązanie niektórych pytań, które mogą wystąpić.

## <a name="whats-the-difference-between-legacy-fxcop-and-net-analyzers"></a>Jaka jest różnica między starszymi analizatorami FxCop i .NET?

Starsza FxCop uruchamia analizę po kompilacji dla skompilowanego zestawu. Działa jako oddzielny plik wykonywalny o nazwie **FxCopCmd.exe**. FxCopCmd.exe ładuje skompilowany zestaw, uruchamia analizę kodu, a następnie raportuje wyniki (lub *diagnostykę*).

Analizatory .NET są oparte na .NET Compiler Platform ("Roslyn"). Można [je włączyć z zestawu SDK platformy .NET lub zainstalować jako pakiet NuGet](install-net-analyzers.md) , do którego odwołuje się projekt lub rozwiązanie. Analizatory uruchamiają analizę opartą na kodzie źródłowym podczas wykonywania kompilatora. Analizatory są hostowane w procesie kompilatora, **csc.exe** lub **vbc.exe** i przeprowadzają analizę podczas kompilowania projektu. Wyniki analizatora są raportowane wraz z wynikami kompilatora.

## <a name="whats-the-difference-between-fxcop-analyzers-and-net-analyzers"></a>Jaka jest różnica między analizatorami FxCop i analizatorami .NET?

Zarówno analizatory FxCopy, jak i analizatorze .NET odnoszą się .NET Compiler Platform do implementacji usługi FxCop dla usługi Roslyn. W systemach starszych niż Visual Studio 2019 16,8 i .NET 5,0 te analizatory są dostarczane jako `Microsoft.CodeAnalysis.FxCopAnalyzers` [pakiet NuGet](https://www.nuget.org/packages/Microsoft.CodeAnalysis.FxCopAnalyzers). Począwszy od programu Visual Studio 2019 16,8 i .NET 5,0, te analizatory są [dołączone do zestawu .NET SDK](/dotnet/fundamentals/code-analysis/overview). Są one również dostępne jako `Microsoft.CodeAnalysis.NetAnalyzers` [pakiet NuGet](https://www.nuget.org/packages/Microsoft.CodeAnalysis.NetAnalyzers). Rozważ [przeprowadzenie migracji z analizatorów FxCop do analizatorów platformy .NET](migrate-from-fxcop-analyzers-to-net-analyzers.md).

## <a name="does-the-run-code-analysis-command-run-net-analyzers"></a>Czy polecenie Run Code Analysis uruchamia analizatory .NET?

Przed wydaniem programu Visual Studio 2019 16,5 w przypadku wybrania opcji **Analizuj**  >  **analizę kodu uruchamiania** zostanie wykonana Starsza analiza. Uruchamianie programu Visual Studio 2019 16,5, opcja **uruchamiania analizy kodu** wykonuje analizatory oparte na Roslyn dla wybranego projektu lub rozwiązania. Jeśli zainstalowano analizatory .NET, również zostaną one wykonane. Aby uzyskać więcej informacji, zobacz [jak: uruchamiać analizę kodu ręcznie dla kodu zarządzanego](how-to-run-code-analysis-manually-for-managed-code.md).

## <a name="does-the-runcodeanalysis-msbuild-project-property-run-analyzers"></a>Czy właściwość projektu MSBuild RunCodeAnalysis jest uruchamiana analizatory?

Nie. Właściwość **RunCodeAnalysis** w pliku projektu (na przykład *. csproj*) jest używana tylko do wykonywania starszych FxCop. Uruchamia zadanie programu MSBuild po kompilacji, które wywołuje **FxCopCmd.exe**.

## <a name="so-how-do-i-run-net-analyzers-then"></a>Jak uruchomić analizatory .NET?

Aby uruchomić analizatory .NET, najpierw [Włącz je z zestawu .NET SDK lub zainstaluj jako pakiet NuGet](install-net-analyzers.md). Następnie Skompiluj projekt lub rozwiązanie z programu Visual Studio lub przy użyciu programu MSBuild. Ostrzeżenia i błędy generowane przez analizatory Roslyn będą wyświetlane w **Lista błędów** lub w oknie wiersza polecenia.

## <a name="i-get-warning-ca0507-even-after-ive-installed-the-net-analyzers-nuget-package"></a>Otrzymuję ostrzeżenie CA0507 nawet po zainstalowaniu pakietu NuGet analizatorów .NET

Jeśli zainstalowano analizatory .NET, ale nadal pojawia się ostrzeżenie CA0507 **"" Uruchomienie analizy kodu "zostało zaniechane na rzecz analizatorów FxCop, które są uruchamiane podczas kompilacji"**, może być konieczne ustawienie właściwości programu MSBuild **RunCodeAnalysis** w [pliku projektu](../ide/solutions-and-projects-in-visual-studio.md#project-file) na **false**. W przeciwnym razie Starsza analiza zostanie wykonana po każdej kompilacji.

```xml
<RunCodeAnalysis>false</RunCodeAnalysis>
```

## <a name="which-rules-have-been-ported-to-net-analyzers"></a>Które reguły zostały przeanalizowane do analizatorów .NET?

Aby uzyskać informacje o tym, które starsze reguły analizy zostały przeanalizowane do analizatorów .NET, zobacz [stan portu reguły FxCop](fxcop-rule-port-status.md).

## <a name="code-analysis-warnings-are-treated-as-errors"></a>Ostrzeżenia analizy kodu są traktowane jako błędy

Jeśli projekt używa opcji kompilacja do traktowania ostrzeżeń jako błędów, ostrzeżenia analizatora mogą pojawić się jako błędy. Aby zapobiec potraktowaniu ostrzeżeń analizy kodu jako błędów, wykonaj kroki opisane w temacie [Analiza kodu — często zadawane pytania](../code-quality/analyzers-faq.md#treat-warnings-as-errors).

## <a name="see-also"></a>Zobacz też

- [Omówienie analizatorów .NET Compiler Platform](roslyn-analyzers-overview.md)
- [Migrowanie do analizatorów .NET](migrate-from-legacy-analysis-to-net-analyzers.md)
- [Zainstaluj analizatory .NET](install-net-analyzers.md)
