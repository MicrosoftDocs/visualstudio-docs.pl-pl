---
title: EditorConfig a analizatory
ms.date: 03/11/2019
ms.topic: conceptual
helpviewer_keywords:
- analyzers, faq
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 12e6681490c6c933369d3fef064ec88f240e3a99
ms.sourcegitcommit: b23d73c86ec7720c4cd9a58050860bc559623a3d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/09/2019
ms.locfileid: "72172771"
---
# <a name="code-analysis-faq"></a>Analiza kodu — często zadawane pytania

Ta strona zawiera odpowiedzi na kilka często zadawanych pytań dotyczących analizy kodu na podstawie .NET Compiler Platform w programie Visual Studio.

## <a name="code-analysis-versus-editorconfig"></a>Analiza kodu w porównaniu z EditorConfig

**P**: Czy należy używać analizy kodu lub EditorConfig do sprawdzania stylu kodu?

ODP **.:** Analiza kodu i pliki EditorConfig są dostępne w ręku. Podczas definiowania stylów kodu [w pliku EditorConfig](../ide/editorconfig-code-style-settings-reference.md) lub na stronie [Opcje edytora tekstu](../ide/code-styles-and-code-cleanup.md) , można faktycznie skonfigurować analizatory kodu, które są wbudowane w program Visual Studio. Pliki EditorConfig mogą służyć do włączania lub wyłączania reguł analizatora, a także do konfigurowania niektórych pakietów analizatora NuGet, takich jak [FxCop](configure-fxcop-analyzers.md).

## <a name="editorconfig-versus-rule-sets"></a>EditorConfig a zestawy reguł

**P**: Czy należy skonfigurować moje analizatory przy użyciu zestawu reguł lub pliku EditorConfig?

ODP **.:** Zestawy reguł i pliki EditorConfig mogą współistnieć i mogą być używane do konfigurowania analizatorów. Zarówno pliki EditorConfig, jak i zestawy reguł umożliwiają włączanie i wyłączanie reguł oraz ustawianie ich ważności.

Jednak pliki EditorConfig oferują dodatkowe sposoby konfigurowania reguł:

- W przypadku analizatorów FxCop pliki EditorConfig umożliwiają [Definiowanie typów kodu do analizy](fxcop-analyzer-options.md).
- W przypadku analizatorów w stylu kodu, które są wbudowane w program Visual Studio, pliki EditorConfig umożliwiają [Definiowanie preferowanych stylów kodu](../ide/editorconfig-code-style-settings-reference.md) dla bazy kodu.

Oprócz zestawów reguł i plików EditorConfig Niektóre analizatory są konfigurowane przy użyciu plików tekstowych oznaczonych jako [dodatkowe pliki](../ide/build-actions.md#build-action-values) dla kompilatorów C# i VB.

> [!NOTE]
> - Plików EditorConfig można używać tylko do włączania reguł i ustawiania ich ważności w programie Visual Studio 2019 w wersji 16,3 lub nowszej.
> - Nie można używać plików EditorConfig do konfigurowania starszej analizy, natomiast zestawy reguł mogą.

## <a name="code-analysis-in-ci-builds"></a>Analiza kodu w kompilacjach CI

**P**: Czy analiza kodu oparta na .NET Compiler Platform działa w kompilacjach ciągłej integracji (CI)?

ODP **.:** Tak. W przypadku analizatorów instalowanych z pakietu NuGet te reguły są [wymuszane w czasie kompilacji](roslyn-analyzers-overview.md#build-errors), w tym w trakcie kompilacji elementu konfiguracji. Analizatory używane w kompilacjach CI respektują konfigurację reguły z obu zestawów reguł i plików EditorConfig. Obecnie analizatory kodu, które są wbudowane w program Visual Studio, nie są dostępne jako pakiet NuGet, dlatego te reguły nie są wymuszane w kompilacji CI.

## <a name="ide-analyzers-versus-stylecop"></a>Analizatory IDE a StyleCop

**P**: Czym różnią się analizatory kodu IDE programu Visual Studio i analizatory StyleCop?

ODP **.:** Środowisko IDE programu Visual Studio zawiera wbudowane analizatory, które szukają zarówno stylu kodu, jak i problemów z jakością. Te reguły ułatwiają korzystanie z nowych funkcji języka w miarę ich wprowadzania i zwiększają łatwość utrzymania kodu. Analizatory IDE są stale aktualizowane wraz z każdą wersją programu Visual Studio.

[Analizatory StyleCop](https://github.com/DotNetAnalyzers/StyleCopAnalyzers) to analizatory innych firm, które są instalowane jako pakiet NuGet, który sprawdza spójność stylu w kodzie. Ogólnie rzecz biorąc, reguły StyleCop umożliwiają ustawianie osobistych preferencji dla bazy kodu bez zalecania stosowania stylu na innym.

## <a name="code-analyzers-versus-legacy-analysis"></a>Analizatory kodu i analiza starszej wersji

**P**: Jaka jest różnica między starszą analizą a analizą kodu na podstawie .NET Compiler Platform?

Odp **.: Analiza kodu oparta na .NET compiler platform**analizuje kod źródłowy w czasie rzeczywistym i podczas kompilacji, natomiast Starsza analiza analizuje pliki binarne po zakończeniu kompilacji. Aby uzyskać więcej informacji, zobacz [Analiza na podstawie .NET compiler platform a Starsza analiza](roslyn-analyzers-overview.md#source-code-analysis-versus-legacy-analysis) i [FxCop — często zadawane pytania](fxcop-analyzers-faq.md).

## <a name="treat-warnings-as-errors"></a>Traktuj ostrzeżenia jako błędy

**P**: Mój projekt używa opcji Build, aby traktować ostrzeżenia jako błędy. Po przeprowadzeniu migracji ze starszej wersji analizy do analizy kodu źródłowego wszystkie ostrzeżenia analizy kodu są teraz wyświetlane jako błędy. Jak mogę to zapobiec?

ODP **.:** Aby zapobiec potraktowaniu ostrzeżeń analizy kodu jako błędów, wykonaj następujące kroki:

  1. Utwórz plik. props o następującej zawartości:

     ```xml
     <Project>
        <PropertyGroup>
           <CodeAnalysisTreatWarningsAsErrors>false</CodeAnalysisTreatWarningsAsErrors>
        </PropertyGroup>
     </Project>
     ```

  2. Dodaj wiersz do pliku projektu. csproj lub. vbproj, aby zaimportować plik. props, który został utworzony w poprzednim kroku. Ten wiersz musi być umieszczony przed wszystkimi wierszami, które zaimportują Analizator FxCop. props Files. Na przykład, jeśli plik. props ma nazwę CodeAnalysis. props:

     ```xml
     ...
     <Import Project="..\..\codeanalysis.props" Condition="Exists('..\..\codeanalysis.props')" />
     <Import Project="..\packages\Microsoft.CodeAnalysis.FxCopAnalyzers.2.6.5\build\Microsoft.CodeAnalysis.FxCopAnalyzers.props" Condition="Exists('..\packages\Microsoft.CodeAnalysis.FxCopAnalyzers.2.6.5\build\Microsoft.CodeAnalysis.FxCopAnalyzers.props')" />
     ...
     ```

## <a name="see-also"></a>Zobacz także

- [Przegląd analizatorów](roslyn-analyzers-overview.md)
- [.NET coding convention ustawienia dla wtyczki EditorConfig](../ide/editorconfig-code-style-settings-reference.md)
