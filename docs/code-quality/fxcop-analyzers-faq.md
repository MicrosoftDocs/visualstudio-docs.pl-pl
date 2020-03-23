---
title: Analiza kodu FxCop i analizatory FxCop
ms.date: 09/06/2018
ms.topic: conceptual
helpviewer_keywords:
- code analysis FAQ
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: bc04cbc6d46d8dc47a08d06c8c5949bb5d9107f3
ms.sourcegitcommit: 92361aac3665a934faa081e1d1ea89a067b01c5b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/17/2020
ms.locfileid: "79431368"
---
# <a name="frequently-asked-questions-about-fxcop-and-fxcop-analyzers"></a>Często zadawane pytania dotyczące analizatorów FxCop i FxCop

To może być trochę mylące, aby zrozumieć różnice między starszych Analizatorów FxCop i FxCop. Ten artykuł ma na celu rozwiązanie niektórych pytań, które możesz mieć.

## <a name="whats-the-difference-between-legacy-fxcop-and-fxcop-analyzers"></a>Jaka jest różnica między starszymi analizatorami FxCop i FxCop?

Legacy FxCop uruchamia analizę po kompilacji na skompilowanym zestawie. Działa jako oddzielny plik wykonywalny o nazwie **FxCopCmd.exe**. FxCopCmd.exe ładuje skompilowany zestaw, uruchamia analizę kodu, a następnie raportuje wyniki (lub *diagnostykę).*

Analizatory FxCop są oparte na platformie kompilatora .NET ("Roslyn"). Zainstaluj [je jako pakiet NuGet,](install-fxcop-analyzers.md#nuget-package) do którego odwołuje się projekt lub rozwiązanie. Analizatory FxCop uruchamiają analizę opartą na kodzie źródłowym podczas wykonywania kompilatora. Analizatory FxCop są hostowane w procesie kompilatora, **csc.exe** lub **vbc.exe**i uruchamiają analizę po zbudowaniu projektu. Wyniki analizatora są zgłaszane wraz z wynikami kompilatora.

> [!NOTE]
> [Analizatory FxCop](install-fxcop-analyzers.md#vsix)można również zainstalować jako rozszerzenie programu Visual Studio. W takim przypadku analizatory wykonać podczas wpisywać w edytorze kodu, ale nie są one wykonywane w czasie kompilacji. Jeśli chcesz uruchomić analizatory FxCop w ramach ciągłej integracji (CI), zainstaluj je jako pakiet NuGet zamiast tego.

## <a name="does-the-run-code-analysis-command-run-fxcop-analyzers"></a>Czy polecenie Uruchom analizę kodu uruchamia analizatory FxCop?

Przed wydaniem programu Visual Studio 2019 16.5, po **wybraniu opcji Analizuj** > **analizę kodu uruchamiania,** wykonuje starszą analizę. Uruchamianie programu Visual Studio 2019 16.5, uruchom **analizę kodu** menu opcja wykonuje analizatory oparte na Roslyn dla wybranego projektu lub rozwiązania. Jeśli zainstalowano analizatory FxCop oparte na Roslyn, będą one również wykonywane. Aby uzyskać więcej informacji, zobacz [Jak: Ręcznie uruchamiać analizę kodu dla kodu zarządzanego](how-to-run-code-analysis-manually-for-managed-code.md).

## <a name="does-the-runcodeanalysis-msbuild-project-property-run-analyzers"></a>Czy RunCodeAnalysis msbuild właściwości projektu uruchomić analizatory?

Nie. **Właściwość RunCodeAnalysis** w pliku projektu (na przykład *.csproj)* jest używana tylko do wykonywania starszego fxcopa. Uruchamia zadanie msbuild po kompilacji, które wywołuje **FxCopCmd.exe**.

## <a name="so-how-do-i-run-fxcop-analyzers-then"></a>Więc jak uruchomić analizatory FxCop wtedy?

Aby uruchomić analizatory FxCop, najpierw zainstaluj dla nich [pakiet NuGet.](install-fxcop-analyzers.md) Następnie skompiluj projekt lub rozwiązanie z programu Visual Studio lub przy użyciu msbuild. Ostrzeżenia i błędy generowane przez analizatory FxCop pojawią się na **liście błędów** lub w oknie polecenia.

## <a name="i-get-warning-ca0507-even-after-ive-installed-the-fxcop-analyzers-nuget-package"></a>Otrzymuję ostrzeżenie CA0507 nawet po zainstalowaniu pakietu Analizatorów FxCop NuGet

Jeśli masz zainstalowane analizatory FxCop, ale nadal otrzymywać ostrzeżenie CA0507 **""Uruchom analizę kodu" został przestarzały na rzecz analizatorów FxCop, które działają podczas kompilacji,** może być konieczne ustawienie **RunCodeAnalysis** msbuild właściwość w [pliku projektu](../ide/solutions-and-projects-in-visual-studio.md#project-file) do **false**. W przeciwnym razie starsza analiza zostanie wykonana po każdej kompilacji.

```xml
<RunCodeAnalysis>false</RunCodeAnalysis>
```

## <a name="which-rules-have-been-ported-to-fxcop-analyzers"></a>Które reguły zostały przeniesione do analizatorów FxCop?

Aby uzyskać informacje o tym, które starsze reguły analizy zostały przeniesione do [analizatorów FxCop,](install-fxcop-analyzers.md)zobacz [Stan portu reguły Fxcop](fxcop-rule-port-status.md).

## <a name="code-analysis-warnings-are-treated-as-errors"></a>Ostrzeżenia dotyczące analizy kodu są traktowane jako błędy

Jeśli projekt używa opcji kompilacji do traktowania ostrzeżeń jako błędów, ostrzeżenia analizatora FxCop mogą być wyświetlane jako błędy. Aby zapobiec traktowaniu ostrzeżeń o analizie kodu jako błędów, wykonaj kroki opisane w [często zadawanych pytaniach dotyczących analizy kodu.](../code-quality/analyzers-faq.md#treat-warnings-as-errors)

## <a name="see-also"></a>Zobacz też

- [Omówienie analizatorów platformy kompilatora .NET](roslyn-analyzers-overview.md)
- [Migrowanie do analizatorów FxCop](migrate-from-legacy-analysis-to-fxcop-analyzers.md)
- [Instalowanie analizatorów FxCop](install-fxcop-analyzers.md)
