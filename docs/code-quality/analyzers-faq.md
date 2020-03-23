---
title: EditorConfig kontra analizatory
ms.date: 03/11/2019
ms.topic: conceptual
helpviewer_keywords:
- analyzers, faq
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 680d52ff04553d399b6abeb53919d8aafd4fa792
ms.sourcegitcommit: 95f26af1da51d4c83ae78adcb7372b32364d8a2b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/13/2020
ms.locfileid: "79301693"
---
# <a name="code-analysis-faq"></a>Analiza kodu — często zadawane pytania

Ta strona zawiera odpowiedzi na niektóre często zadawane pytania dotyczące analizy kodu opartej na platformie kompilatora platformy .NET w programie Visual Studio.

## <a name="code-analysis-versus-editorconfig"></a>Analiza kodu a EditorConfig

**P:** Czy należy używać analizy kodu lub EditorConfig do sprawdzania stylu kodu?

**A:** Analiza kodu i EditorConfig pliki pracy ręka w rękę. Podczas definiowania stylów kodu [w editorconfig pliku](../ide/editorconfig-code-style-settings-reference.md) lub na stronie [Opcje edytora tekstu,](../ide/code-styles-and-code-cleanup.md) jesteś faktycznie konfigurowania analizatorów kodu, które są wbudowane w programie Visual Studio. EditorConfig pliki mogą być używane do włączania lub wyłączania reguł analizatora, a także do konfigurowania niektórych pakietów analizatorów NuGet, takich jak [analizatory FxCop](configure-fxcop-analyzers.md).

## <a name="editorconfig-versus-rule-sets"></a>EditorConfig kontra zestawy reguł

**P:** Czy należy skonfigurować analizatory przy użyciu zestawu reguł lub pliku EditorConfig?

**A:** Zestawy reguł i EditorConfig pliki mogą współistnieć i mogą być używane do konfigurowania analizatorów. Zarówno EditorConfig plików i zestawów reguł pozwalają włączyć i wyłączyć reguły i ustawić ich ważność.

Jednak editorconfig pliki oferują dodatkowe sposoby konfigurowania reguł zbyt:

- Dla analizatorów FxCop, EditorConfig pliki pozwalają [określić, które typy kodu do analizy](fxcop-analyzer-options.md).
- Dla analizatorów stylu kodu, które są wbudowane w programie Visual Studio, EditorConfig plików umożliwiają [definiowanie preferowanych stylów kodu](../ide/editorconfig-code-style-settings-reference.md) dla bazy kodu.

Oprócz zestawów reguł i plików EditorConfig, niektóre analizatory są konfigurowane za pomocą plików tekstowych oznaczonych jako [dodatkowe pliki](../ide/build-actions.md#build-action-values) dla kompilatorów C# i VB.

> [!NOTE]
> - EditorConfig pliki mogą służyć tylko do włączania reguł i ustawić ich ważność w programie Visual Studio 2019 w wersji 16.3 i nowszych.
> - EditorConfig plików nie można użyć do konfigurowania starszej analizy, podczas gdy zestawy reguł mogą.

## <a name="code-analysis-in-ci-builds"></a>Analiza kodu w kompilacjach ci

**P:** Czy analiza kodu oparta na platformie kompilatora .NET działa w kompilacjach ciągłej integracji (CI)?

**A:** Tak. Dla analizatorów, które są instalowane z pakietu NuGet, te reguły są [wymuszane w czasie kompilacji,](roslyn-analyzers-overview.md#build-errors)w tym podczas kompilacji ci. Analizatory używane w ci kompilacje szanować konfigurację reguły z obu zestawów reguł i EditorConfig plików. Obecnie analizatory kodu, które są wbudowane w programie Visual Studio nie są dostępne jako pakiet NuGet, a więc te reguły nie są wymuszane w kompilacji ciągłej integracji.

## <a name="ide-analyzers-versus-stylecop"></a>Analizatory IDE a StyleCop

**Q**Pyt.: Jaka jest różnica między analizatory kodu IDE programu Visual Studio i analizatory StyleCop?

**A:** Ide programu Visual Studio zawiera wbudowane analizatory, które szukają zarówno styl kodu i problemy z jakością. Te reguły ułatwiają korzystanie z nowych funkcji języka, ponieważ są one wprowadzane i poprawić łatwość konserwacji kodu. Analizatory IDE są stale aktualizowane przy każdej wersji programu Visual Studio.

[Analizatory StyleCop](https://github.com/DotNetAnalyzers/StyleCopAnalyzers) są analizatory innych firm zainstalowane jako pakiet NuGet, które sprawdzają spójność stylu w kodzie. Ogólnie rzecz biorąc reguły StyleCop umożliwiają ustawianie osobistych preferencji dla bazy kodu bez zalecania jednego stylu nad innym.

## <a name="code-analyzers-versus-legacy-analysis"></a>Analizatory kodu a starsza analiza

**P:** Jaka jest różnica między starszą analizą a analizą kodu opartą na platformie kompilatora .NET?

**A:**.NET Compiler Platform analizy kodu analizy kodu w czasie rzeczywistym i podczas kompilacji, podczas gdy starsza analiza analizuje pliki binarne po zakończeniu kompilacji. Aby uzyskać więcej informacji, zobacz [analiza oparta na platformie kompilatora .NET i starsza analiza](roslyn-analyzers-overview.md#source-code-analysis-versus-legacy-analysis) oraz [często zadawane pytania dotyczące analizatorów FxCop.](fxcop-analyzers-faq.md)

## <a name="treat-warnings-as-errors"></a>Traktuj ostrzeżenia jako błędy

**P:** Mój projekt używa opcji kompilacji do traktowania ostrzeżeń jako błędów. Po migracji z analizy starszej do analizy kodu źródłowego wszystkie ostrzeżenia analizy kodu są teraz wyświetlane jako błędy. Jak mogę temu zapobiec?

**A:** Aby zapobiec traktowaniu ostrzeżeń analizy kodu jako błędów, wykonaj następujące kroki:

  1. Utwórz plik .props o następującej zawartości:

     ```xml
     <Project>
        <PropertyGroup>
           <CodeAnalysisTreatWarningsAsErrors>false</CodeAnalysisTreatWarningsAsErrors>
        </PropertyGroup>
     </Project>
     ```

  2. Dodaj wiersz do pliku projektu csproj lub .vbproj, aby zaimportować plik .props utworzony w poprzednim kroku. Ten wiersz musi być umieszczony przed wierszami importu plików .props analizatora FxCop. Na przykład, jeśli plik .props nosi nazwę codeanalysis.props:

     ```xml
     ...
     <Import Project="..\..\codeanalysis.props" Condition="Exists('..\..\codeanalysis.props')" />
     <Import Project="..\packages\Microsoft.CodeAnalysis.FxCopAnalyzers.2.6.5\build\Microsoft.CodeAnalysis.FxCopAnalyzers.props" Condition="Exists('..\packages\Microsoft.CodeAnalysis.FxCopAnalyzers.2.6.5\build\Microsoft.CodeAnalysis.FxCopAnalyzers.props')" />
     ...
     ```

## <a name="see-also"></a>Zobacz też

- [Omówienie analizatorów](roslyn-analyzers-overview.md)
- [Ustawienia konwencji kodowania .NET dla EditorConfig](../ide/editorconfig-code-style-settings-reference.md)
