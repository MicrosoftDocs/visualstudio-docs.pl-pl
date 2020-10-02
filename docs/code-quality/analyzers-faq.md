---
title: EditorConfig a analizatory
ms.date: 03/11/2019
ms.topic: conceptual
helpviewer_keywords:
- analyzers, faq
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 134f91531b9485f5a887b2d9785a490fcea605fc
ms.sourcegitcommit: c025a5e2013c4955ca685092b13e887ce64aaf64
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/02/2020
ms.locfileid: "91659169"
---
# <a name="code-analysis-faq"></a>Analiza kodu — często zadawane pytania

Ta strona zawiera odpowiedzi na kilka często zadawanych pytań dotyczących analizy kodu na podstawie .NET Compiler Platform w programie Visual Studio.

## <a name="code-analysis-versus-editorconfig"></a>Analiza kodu w porównaniu z EditorConfig

**P**: czy należy użyć analizy kodu lub EditorConfig do sprawdzania stylu kodu?

Odp **.: Analiza**kodu i pliki EditorConfig są dostępne w ręku. Podczas definiowania stylów kodu [w pliku EditorConfig](/dotnet/fundamentals/code-analysis/code-style-rule-options) lub na stronie [Opcje edytora tekstu](../ide/code-styles-and-code-cleanup.md) , można faktycznie skonfigurować analizatory kodu, które są wbudowane w program Visual Studio. Pliki EditorConfig mogą służyć do włączania lub wyłączania reguł analizatora, a także do konfigurowania pakietów analizatora NuGet.

## <a name="editorconfig-versus-rule-sets"></a>EditorConfig a zestawy reguł

**P**: czy należy skonfigurować moje analizatory przy użyciu zestawu reguł lub pliku EditorConfig?

Odp **.: zestawy**reguł i pliki EditorConfig mogą współistnieć i mogą być używane do konfigurowania analizatorów. Zarówno pliki EditorConfig, jak i zestawy reguł umożliwiają włączanie i wyłączanie reguł oraz ustawianie ich ważności.

Jednak pliki EditorConfig oferują dodatkowe sposoby konfigurowania reguł:

- W przypadku analizatorów jakości kodu platformy .NET pliki EditorConfig umożliwiają [Definiowanie typów kodu do analizy](/dotnet/fundamentals/code-analysis/code-quality-rule-options).
- W przypadku analizatorów stylu kodu platformy .NET wbudowanych w program Visual Studio pliki EditorConfig umożliwiają [Definiowanie preferowanych stylów kodu](/dotnet/fundamentals/code-analysis/code-style-rule-options) dla bazy kodu.

Oprócz zestawów reguł i plików EditorConfig Niektóre analizatory są konfigurowane przy użyciu plików tekstowych oznaczonych jako [dodatkowe pliki](../ide/build-actions.md#build-action-values) dla kompilatorów C# i VB.

> [!NOTE]
> - Plików EditorConfig można używać tylko do włączania reguł i ustawiania ich ważności w programie Visual Studio 2019 w wersji 16,3 lub nowszej.
> - Nie można używać plików EditorConfig do konfigurowania starszej analizy, natomiast zestawy reguł mogą.

## <a name="code-analysis-in-ci-builds"></a>Analiza kodu w kompilacjach CI

**P**: czy analiza kodu oparta na .NET compiler platform jest zgodna z kompilacjami ciągłej integracji (ci)?

Odp **.: tak**. W przypadku analizatorów instalowanych z pakietu NuGet te reguły są [wymuszane w czasie kompilacji](roslyn-analyzers-overview.md#build-errors), w tym w trakcie kompilacji elementu konfiguracji. Analizatory używane w kompilacjach CI respektują konfigurację reguły z obu zestawów reguł i plików EditorConfig. Obecnie analizatory kodu, które są wbudowane w program Visual Studio, nie są dostępne jako pakiet NuGet, dlatego te reguły nie są wymuszane w kompilacji CI.

## <a name="ide-analyzers-versus-stylecop"></a>Analizatory IDE a StyleCop

**P**: Jaka jest różnica między analizatorami kodu IDE programu Visual Studio i analizatorami StyleCop?

Odp **.: środowisko IDE programu Visual**Studio zawiera wbudowane analizatory, które szukają zarówno stylu kodu, jak i problemów z jakością. Te reguły ułatwiają korzystanie z nowych funkcji języka w miarę ich wprowadzania i zwiększają łatwość utrzymania kodu. Analizatory IDE są stale aktualizowane wraz z każdą wersją programu Visual Studio.

[Analizatory StyleCop](https://github.com/DotNetAnalyzers/StyleCopAnalyzers) to analizatory innych firm, które są instalowane jako pakiet NuGet, który sprawdza spójność stylu w kodzie. Ogólnie rzecz biorąc, reguły StyleCop umożliwiają ustawianie osobistych preferencji dla bazy kodu bez zalecania stosowania stylu na innym.

## <a name="code-analyzers-versus-legacy-analysis"></a>Analizatory kodu i analiza starszej wersji

**P**: Jaka jest różnica między starszą analizą a analizą kodu opartą na .NET compiler platform?

Odp **.: Analiza kodu oparta na .NET compiler platform**analizuje kod źródłowy w czasie rzeczywistym i podczas kompilacji, natomiast Starsza analiza analizuje pliki binarne po zakończeniu kompilacji. Aby uzyskać więcej informacji, zobacz [Analiza oparta na .NET compiler platformach i analiza starszej wersji](../code-quality/fxcop-analyzers-faq.md#whats-the-difference-between-legacy-fxcop-and-fxcop-analyzers).

## <a name="treat-warnings-as-errors"></a>Traktuj ostrzeżenia jako błędy

**P**: mój projekt używa opcji Build, aby traktować ostrzeżenia jako błędy. Po przeprowadzeniu migracji ze starszej wersji analizy do analizy kodu źródłowego wszystkie ostrzeżenia analizy kodu są teraz wyświetlane jako błędy. Jak mogę to zapobiec?

Odp **.: aby**zapobiec potraktowaniu ostrzeżeń analizy kodu jako błędów, wykonaj następujące czynności:

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

## <a name="code-analysis-solution-property-page"></a>Strona właściwości rozwiązania analizy kodu

**P**: gdzie jest stroną właściwości analizy kodu dla rozwiązania?

Odp **.: Strona**właściwości Analiza kodu na poziomie rozwiązania została usunięta na korzyść grupy wspólnych właściwości. Aby zarządzać analizą kodu na poziomie projektu, Strona właściwości Analiza kodu jest nadal dostępna. (W przypadku projektów zarządzanych zalecamy także Migrowanie z zestawów reguł do EditorConfig dla konfiguracji reguł).  W celu udostępniania zestawów reguł w wielu/wszystkich projektach w rozwiązaniu lub repozytorium zaleca się zdefiniowanie grupy właściwości z właściwością CodeAnalysisRuleSet w udostępnionym pliku props/targets lub katalogu. props/Directory. targets. Jeśli nie masz żadnych takich wspólnych właściwości lub obiektów docelowych, które zostały zaimportowane przez wszystkie projekty, rozważ [dodanie takiej grupy właściwości do katalogu. props lub Directory. targets w katalogu rozwiązania najwyższego poziomu, który jest automatycznie importowany we wszystkich plikach projektu zdefiniowanych w katalogu lub jego podkatalogach](../msbuild/customize-your-build.md).

## <a name="see-also"></a>Zobacz też

- [Przegląd analizatorów](roslyn-analyzers-overview.md)
- [Ustawienia konwencji kodowania .NET dla EditorConfig](/dotnet/fundamentals/code-analysis/code-style-rule-options)