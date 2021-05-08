---
title: Analiza kodu FxCop (analiza binarna) i analizatory .NET (analiza źródła)
ms.date: 09/06/2018
description: Poznaj różnicę między starszymi analizatorami FxCop (analiza binarna) i .NET (analiza źródła) w Visual Studio. Zapoznaj się z odpowiedziami na pytania dotyczące używania tych analizatorów.
ms.custom: SEO-VS-2020
ms.topic: conceptual
helpviewer_keywords:
- code analysis FAQ
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- dotnet
ms.openlocfilehash: 951e9b951f1d90077fe29506e9c288fb19f2d5ff
ms.sourcegitcommit: dd2fc6e03a789c044f8438096b8f112e4dba5557
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/06/2021
ms.locfileid: "108800505"
---
# <a name="frequently-asked-questions-about-legacy-fxcop-and-net-analyzers"></a>Często zadawane pytania dotyczące starszych analizatorów FxCop i .NET

Zrozumienie różnic między starszymi analizatorami FxCop (analiza binarna) i analizatorami .NET (analiza źródła) może być nieco mylące. Ten artykuł ma na celu odpowiedzi na niektóre pytania, które mogą się pojawić.

## <a name="whats-the-difference-between-legacy-fxcop-and-net-analyzers"></a>Jaka jest różnica między starszymi analizatorami FxCop i .NET?

Starsza wersja rozwiązania FxCop uruchamia analizę po kompilacji na skompilowanym zestawie. Jest on uruchamiany jako oddzielny plik wykonywalny o **nazwieFxCopCmd.exe**. FxCopCmd.exe zestaw skompilowany, uruchamia analizę kodu, a następnie raportuje wyniki (lub *diagnostykę).*

Analizatory .NET są oparte na .NET Compiler Platform ("Roslyn"). Można [je włączyć z zestawu .NET SDK](install-net-analyzers.md) lub zainstalować jako pakiet NuGet, do których odwołuje się projekt lub rozwiązanie. Analizatory uruchamiają analizę opartą na kodzie źródłowym podczas wykonywania kompilatora. Analizatory są hostowane w  ramach procesu kompilatora,csc.exelub **vbc.exe**, i uruchamiają analizę podczas tworzenia projektu. Wyniki analizatora są raportowane wraz z wynikami kompilatora.

## <a name="whats-the-difference-between-fxcop-analyzers-and-net-analyzers"></a>Jaka jest różnica między analizatorami FxCop i analizatorami .NET?

Zarówno analizatory FxCop, jak i analizatory .NET odnoszą się .NET Compiler Platform ("Roslyn") do implementacji reguł urzędu certyfikacji FxCop. Przed Visual Studio 2019 r. 16.8 i .NET 5.0 te analizatory były dostarczane jako `Microsoft.CodeAnalysis.FxCopAnalyzers` [pakiet NuGet](https://www.nuget.org/packages/Microsoft.CodeAnalysis.FxCopAnalyzers). Począwszy od Visual Studio 2019 r. 16.8 i .NET 5.0, te analizatory są dołączone do [zestawu SDK platformy .NET.](/dotnet/fundamentals/code-analysis/overview) Są one również dostępne jako `Microsoft.CodeAnalysis.NetAnalyzers` [pakiet NuGet.](https://www.nuget.org/packages/Microsoft.CodeAnalysis.NetAnalyzers) Rozważ [migrowanie z analizatorów FxCop do analizatorów .NET.](migrate-from-fxcop-analyzers-to-net-analyzers.md)

## <a name="does-the-run-code-analysis-command-run-net-analyzers"></a>Czy polecenie Uruchom Code Analysis uruchamia analizatory .NET?

Przed wydaniem Visual Studio 2019 16.5 wybranie opcji Przeanalizuj przebieg Code Analysis umożliwia wykonanie  >  starszej analizy. Począwszy Visual Studio 2019 r. 16.5,  opcja menu Uruchom Code Analysis wykonuje analizatory oparte na platformie Roslyn dla wybranego projektu lub rozwiązania. Jeśli zainstalowano analizatory .NET, zostaną one również wykonane. Aby uzyskać więcej informacji, [zobacz How to: Run Code Analysis Manually for Managed Code](how-to-run-code-analysis-manually-for-managed-code.md)(Jak ręcznie uruchomić kod zarządzany).

## <a name="does-the-runcodeanalysis-msbuild-project-property-run-analyzers"></a>Czy właściwości projektu RunCodeAnalysis programu msbuild uruchamiają analizatory?

Nie. Właściwość **RunCodeAnalysis** w pliku projektu (na przykład *csproj*) jest używana tylko do wykonywania starszej wersji programu FxCop. Uruchamia zadanie msbuild po kompilacji, które wywołujeFxCopCmd.exe **.**

## <a name="so-how-do-i-run-net-analyzers-then"></a>Jak więc uruchomić analizatory .NET?

Aby uruchomić analizatory .NET, najpierw włącz je z zestawu .NET SDK lub zainstaluj [je jako pakiet NuGet.](install-net-analyzers.md) Następnie skompilować projekt lub rozwiązanie z Visual Studio lub przy użyciu programu msbuild. Ostrzeżenia i błędy generowane przez analizatory Roslyn będą wyświetlane na liście błędów **lub** w oknie polecenia.

## <a name="i-get-warning-ca0507-even-after-ive-installed-the-net-analyzers-nuget-package"></a>Ostrzeżenie CA0507 jest wyświetlane nawet po zainstalowaniu pakietu NuGet analizatorów .NET

Jeśli zainstalowano analizatory .NET, ale nadal wyświetlane jest ostrzeżenie CA0507 "Uruchom Code Analysis" zostało wycofane na rzecz analizatorów **FxCop uruchamianych** podczas kompilacji", może [](../ide/solutions-and-projects-in-visual-studio.md#project-file) być konieczne ustawienie właściwości **RunCodeAnalysis** msbuild w pliku projektu na wartość **false**. W przeciwnym razie starsza analiza będzie wykonywana po każdej kompilacji.

```xml
<RunCodeAnalysis>false</RunCodeAnalysis>
```

## <a name="which-rules-have-been-ported-to-net-analyzers"></a>Które reguły zostały przeportowane do analizatorów .NET?

Aby uzyskać informacje o tym, które starsze reguły analizy zostały przeportowane do analizatorów .NET, zobacz [Fxcop rule port status (Stan portu reguły Fxcop).](fxcop-rule-port-status.md)

## <a name="code-analysis-warnings-are-treated-as-errors"></a>Ostrzeżenia analizy kodu są traktowane jako błędy

Jeśli projekt używa opcji kompilacji do traktowania ostrzeżeń jako błędów, ostrzeżenia analizatora mogą być wyświetlane jako błędy. Aby zapobiec traktowaniu ostrzeżeń analizy kodu jako błędów, wykonaj kroki opisane w artykule [Analiza kodu — często zadawane pytania.](../code-quality/analyzers-faq.md#treat-warnings-as-errors)

## <a name="see-also"></a>Zobacz też

- [Omówienie analizatorów .NET Compiler Platform danych](roslyn-analyzers-overview.md)
- [Przechodzenie na analizatory .NET](migrate-from-legacy-analysis-to-net-analyzers.md)
- [Instalowanie analizatorów .NET](install-net-analyzers.md)
