---
title: Analiza kodu programu FxCop i analizatory FxCop analizujące kod
ms.date: 09/06/2018
ms.topic: overview
helpviewer_keywords:
- code analysis FAQ
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 1634731e68c395dea5a14876cf67944714cb4c3a
ms.sourcegitcommit: 87d7123c09812534b7b08743de4d11d6433eaa13
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/01/2019
ms.locfileid: "57222492"
---
# <a name="frequently-asked-questions-about-fxcop-and-fxcop-analyzers"></a>Często zadawane pytania dotyczące programu FxCop i FxCop analizatorów

Może być nieco mylące zrozumieć różnice między starszej wersji programu FxCop i FxCop analizatorów. Ten artykuł ma na celu niektórych pytań, które może mieć adres.

## <a name="whats-the-difference-between-legacy-fxcop-and-fxcop-analyzers"></a>Jaka jest różnica między starszej wersji programu FxCop i FxCop analizatory?

Starszej wersji programu FxCop działa analizy po kompilacji w skompilowanym zestawie. Jest uruchamiana jako oddzielny plik wykonywalny, o nazwie **FxCopCmd.exe**. FxCopCmd.exe ładuje skompilowanego zestawu, przeprowadza analizy kodu i następnie przedstawia wyniki (lub *diagnostyki*).

Analizatory FxCop analizujące kod opierają się na platformie kompilatora .NET ("Roslyn"). Możesz [je zainstalować jako pakiet NuGet](install-fxcop-analyzers.md#to-install-fxcop-analyzers-as-a-nuget-package) która odwołuje się projekt lub rozwiązanie. Analizatory FxCop analizujące kod, uruchom kod źródłowy na podstawie analizy podczas wykonywania kompilatora. Analizatory FxCop analizujące kod znajdują się w ramach procesu kompilatora albo **csc.exe** lub **vbc.exe**, i przeprowadzanie analizy, gdy projekt jest kompilowany. Wyniki analizatora są zgłaszane wraz z kompilatora wyników.

> [!NOTE]
> Możesz również [zainstalować analizatory FxCop analizujące kod jako rozszerzenie programu Visual Studio](install-fxcop-analyzers.md#to-install-fxcop-analyzers-as-a-vsix). W tym przypadku analizatorów wykonać podczas wpisywania w edytorze kodu, ale nie są wykonywane w czasie kompilacji. Jeśli chcesz uruchomić analizatory FxCop analizujące kod w ramach ciągłej integracji (CI), zainstaluj je jako pakiet NuGet zamiast tego.

## <a name="does-the-run-code-analysis-command-run-fxcop-analyzers"></a>Polecenie Uruchom analizę kodu, czy działa analizatory FxCop analizujące kod?

Nie. Po wybraniu **analizy** > **Uruchom analizę kodu**, wykonuje statycznej analizy kodu lub starszej wersji programu FxCop. **Przeprowadź analizę kodu** nie ma wpływu na oparte na programie Roslyn analizatorów, w tym analizatory FxCop oparte na programie Roslyn.

## <a name="does-the-runcodeanalysis-msbuild-project-property-run-analyzers"></a>Właściwości projektu programu msbuild RunCodeAnalysis przeprowadza analizatory?

Nie. **RunCodeAnalysis** właściwość w pliku projektu (na przykład *.csproj*) jest używana tylko w celu uruchomienia starszej wersji programu FxCop. Uruchamia zadanie msbuild po kompilacji, który wywołuje **FxCopCmd.exe**. Jest to równoważne z wybraniu **analizy** > **Uruchom analizę kodu** w programie Visual Studio.

## <a name="so-how-do-i-run-fxcop-analyzers-then"></a>W jaki sposób następnie uruchomić analizatory FxCop analizujące kod?

Aby uruchomić analizatory FxCop analizujące kod najpierw [zainstaluj pakiet NuGet](install-fxcop-analyzers.md) dla nich. Następnie budowania projektu lub rozwiązania z programu Visual Studio lub za pomocą programu msbuild. Ostrzeżenia i błędy, które generują analizatory FxCop analizujące kod pojawi się w **lista błędów** lub okna poleceń.

## <a name="see-also"></a>Zobacz także

- [Omówienie analizatory platformie kompilatora .NET](roslyn-analyzers-overview.md)
- [Wprowadzenie do analizatorów](fxcop-analyzers.yml)
- [Zainstaluj analizatory FxCop analizujące kod](install-fxcop-analyzers.md)
