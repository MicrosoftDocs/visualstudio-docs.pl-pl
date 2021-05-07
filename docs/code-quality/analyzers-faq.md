---
title: EditorConfig a analizatory
ms.date: 03/11/2019
description: Dowiedz się .NET Compiler Platform analizy kodu opartej na danych w Visual Studio. Zapoznaj się z odpowiedziami na pytania dotyczące plików EditorConfig, zestawów reguł i innych tematów.
ms.custom: SEO-VS-2020
ms.topic: conceptual
helpviewer_keywords:
- analyzers, faq
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 6d67471027f36d0e22c055f4306ce2137d972463
ms.sourcegitcommit: dd2fc6e03a789c044f8438096b8f112e4dba5557
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/06/2021
ms.locfileid: "108800511"
---
# <a name="code-analysis-faq"></a>Analiza kodu — często zadawane pytania

Ta strona zawiera odpowiedzi na niektóre często zadawane pytania dotyczące .NET Compiler Platform na podstawie kodu w Visual Studio.

## <a name="code-analysis-versus-editorconfig"></a>Analiza kodu a EditorConfig

**Pytanie:** Czy do sprawdzania stylu kodu należy użyć analizy kodu lub pliku EditorConfig?

**A:** Pliki Analizy kodu i EditorConfig działają ręcznie. Podczas definiowania stylów kodu w pliku [](../ide/code-styles-and-code-cleanup.md) [EditorConfig](/dotnet/fundamentals/code-analysis/code-style-rule-options) lub na stronie Opcje edytora tekstów w rzeczywistości konfigurujesz analizatory kodu wbudowane w Visual Studio. Pliki EditorConfig mogą służyć do włączania lub wyłączania reguł analizatora, a także do konfigurowania pakietów analizatora NuGet.

## <a name="editorconfig-versus-rule-sets"></a>EditorConfig a zestawy reguł

**Pytanie:** Czy należy skonfigurować analizatory przy użyciu zestawu reguł lub pliku EditorConfig?

**A:** Zestawy reguł i pliki EditorConfig mogą współistnieć i mogą być używane do konfigurowania analizatorów. Zarówno pliki EditorConfig, jak i zestawy reguł umożliwiają włączanie i wyłączanie reguł oraz ustawianie ich ważności.

Jednak pliki EditorConfig oferują również dodatkowe sposoby konfigurowania reguł:

- W przypadku analizatorów jakości kodu .NET pliki EditorConfig umożliwiają zdefiniowanie typów [kodu do przeanalizowania.](/dotnet/fundamentals/code-analysis/code-quality-rule-options)
- W przypadku analizatorów stylu kodu .NET, które są wbudowane w [](/dotnet/fundamentals/code-analysis/code-style-rule-options) Visual Studio, pliki EditorConfig umożliwiają definiowanie preferowanych stylów kodu dla bazy kodu.

Oprócz zestawów reguł i plików EditorConfig niektóre analizatory są konfigurowane [](../ide/build-actions.md#build-action-values) przy użyciu plików tekstowych oznaczonych jako dodatkowe pliki dla kompilatorów C# i VB.

> [!NOTE]
> - Plików EditorConfig można używać tylko do włączania reguł i ustawienia ich ważności w Visual Studio 2019 w wersji 16.3 lub nowszej.
> - Plików EditorConfig nie można używać do konfigurowania starszej analizy, natomiast zestawy reguł mogą.

## <a name="code-analysis-in-ci-builds"></a>Analiza kodu w kompilacjach ci

**Pytanie:** czy .NET Compiler Platform kodu działa w kompilacjach ciągłej integracji?

**Odpowiedź:** Tak. W przypadku analizatorów instalowanych z pakietu NuGet te reguły są wymuszane w czasie [kompilacji,](roslyn-analyzers-overview.md#build-errors)w tym podczas kompilacji ci. Analizatory używane w kompilacjach ciasnych respektują konfigurację reguł zarówno z zestawów reguł, jak i plików EditorConfig. Obecnie analizatory kodu wbudowane w Visual Studio nie są dostępne jako pakiet NuGet, dlatego te reguły nie są wymuszane w kompilacji ci.

## <a name="ide-analyzers-versus-stylecop"></a>Analizatory IDE a styleCop

**Pytanie:** Jaka jest różnica między analizatorami kodu Visual Studio IDE i analizatorami StyleCop?

**A:** Visual Studio IDE zawiera wbudowane analizatory, które szukają zarówno stylu kodu, jak i problemów z jakością. Te reguły ułatwiają korzystanie z nowych funkcji językowych, gdy są wprowadzane, i poprawiają czytelność kodu. Analizatory IDE są stale aktualizowane wraz z każdym Visual Studio wersji.

[Analizatory StyleCop](https://github.com/DotNetAnalyzers/StyleCopAnalyzers) to analizatory innych firm zainstalowane jako pakiet NuGet, które sprawdzają spójność stylu w kodzie. Ogólnie reguły StyleCop umożliwiają ustawianie osobistych preferencji dla bazy kodu bez zalecania jednego stylu od drugiego.

## <a name="code-analyzers-versus-legacy-analysis"></a>Analizatory kodu a starsza analiza

**Pytanie:** Jaka jest różnica między analizą w starszej wersji a .NET Compiler Platform analizy kodu na podstawie kodu?

**Plik**: .NET Compiler Platform analizy kodu analizuje kod źródłowy w czasie rzeczywistym i podczas kompilacji, natomiast starsza analiza analizuje pliki binarne po zakończeniu kompilacji. Aby uzyskać więcej informacji, [zobacz .NET Compiler Platform na podstawie analizy w porównaniu ze starszą analizą.](../code-quality/net-analyzers-faq.md#whats-the-difference-between-legacy-fxcop-and-net-analyzers)

## <a name="fxcop-analyzers-versus-net-analyzers"></a>Analizatory FxCop a analizatory .NET

**Pytanie:** Jaka jest różnica między analizatorami FxCop i analizatorami .NET?

**A:** Zarówno analizatory FxCop, jak i analizatory .NET odnoszą się do .NET Compiler Platform analizatora ("Roslyn") reguł urzędu certyfikacji FxCop. Przed Visual Studio 2019 r. 16.8 i .NET 5.0 te analizatory były dostarczane jako `Microsoft.CodeAnalysis.FxCopAnalyzers` [pakiet NuGet](https://www.nuget.org/packages/Microsoft.CodeAnalysis.FxCopAnalyzers). Począwszy od Visual Studio 2019 r. 16.8 i .NET 5.0, te analizatory są dołączone do [zestawu SDK platformy .NET.](/dotnet/fundamentals/code-analysis/overview) Są one również dostępne jako `Microsoft.CodeAnalysis.NetAnalyzers` [pakiet NuGet.](https://www.nuget.org/packages/Microsoft.CodeAnalysis.NetAnalyzers) Rozważ [migrowanie z analizatorów FxCop do analizatorów .NET.](migrate-from-fxcop-analyzers-to-net-analyzers.md)

## <a name="treat-warnings-as-errors"></a>Traktuj ostrzeżenia jako błędy

**Pytanie:** Mój projekt używa opcji kompilacji, aby traktować ostrzeżenia jako błędy. Po migracji ze starszej analizy do analizy kodu źródłowego wszystkie ostrzeżenia analizy kodu są teraz wyświetlane jako błędy. Jak mogę temu zapobiec?

**A:** Aby zapobiec traktowaniu ostrzeżeń analizy kodu jako błędów, wykonaj następujące kroki:

  1. Utwórz plik props o następującej zawartości:

     ```xml
     <Project>
        <PropertyGroup>
           <CodeAnalysisTreatWarningsAsErrors>false</CodeAnalysisTreatWarningsAsErrors>
        </PropertyGroup>
     </Project>
     ```

  2. Dodaj wiersz do pliku projektu csproj lub vbproj, aby zaimportować plik props utworzony w poprzednim kroku. Ten wiersz należy umieścić przed dowolnymi wierszami, które importują pliki props analizatora. Jeśli na przykład plik props ma nazwę codeanalysis.props:

     ```xml
     ...
     <Import Project="..\..\codeanalysis.props" Condition="Exists('..\..\codeanalysis.props')" />
     <Import Project="..\packages\Microsoft.CodeAnalysis.NetAnalyzers.5.0.0\build\Microsoft.CodeAnalysis.NetAnalyzers.props" Condition="Exists('..\packages\Microsoft.CodeAnalysis.NetAnalyzers.5.0.0\build\Microsoft.CodeAnalysis.NetAnalyzers.props')" />
     ...
     ```

## <a name="code-analysis-solution-property-page"></a>Strona właściwości rozwiązania do analizy kodu

**Pytanie:** gdzie znajduje Code Analysis właściwości rozwiązania?

**A:** strona Code Analysis właściwości na poziomie rozwiązania została usunięta na rzecz bardziej niezawodnej grupy właściwości udostępnionych. Do zarządzania Code Analysis na poziomie projektu strona Code Analysis jest nadal dostępna. (W przypadku projektów zarządzanych zalecamy również migrowanie z zestawu reguł do pliku EditorConfig w celu konfiguracji reguł).  Aby udostępnić zestawy reguł w wielu/wszystkich projektach w rozwiązaniu lub w repo, zalecamy zdefiniowanie grupy właściwości z [właściwością CodeAnalysisRuleSet](../code-quality/using-rule-sets-to-group-code-analysis-rules.md#specify-a-rule-set-for-a-project) w udostępnionym pliku props/targets lub pliku *Directory.props/Directory.targets.* Jeśli nie masz żadnych typowych właściwości lub obiektów docelowych importowanych przez wszystkie projekty, rozważ dodanie takiej grupy właściwości do pliku [Directory.props lub Directory.targets](../msbuild/customize-your-build.md) w katalogu rozwiązania najwyższego poziomu, który jest automatycznie importowany we wszystkich plikach projektu zdefiniowanych w katalogu lub jego podkata folderach.

## <a name="see-also"></a>Zobacz też

- [Omówienie analizatorów](roslyn-analyzers-overview.md)
- [Ustawienia konwencji kodowania .NET dla pliku EditorConfig](/dotnet/fundamentals/code-analysis/code-style-rule-options)