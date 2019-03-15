---
title: Polecenia EditorConfig w porównaniu z analizatorów
ms.date: 03/11/2019
ms.topic: conceptual
helpviewer_keywords:
- analyzers, faq
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: bec9296f15c48cf3b327c78cd0ce7d57adafa002
ms.sourcegitcommit: f7c401a376ce410336846835332a693e6159c551
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2019
ms.locfileid: "57875096"
---
# <a name="analyzers-faq"></a>Analizatory — często zadawane pytania

Ta strona zawiera odpowiedzi na niektóre często zadawane pytania dotyczące analizatorów Roslyn w programie Visual Studio.

## <a name="roslyn-analyzers-versus-editorconfig"></a>Analizatory Roslyn w porównaniu z pliku editorconfig

**Q**: Należy użyć analizatorów Roslyn lub .editorconfig styl kodu?

**A**: Analizatory Roslyn i plików editorconfig pracy ręcznie dostępnych. Podczas definiowania stylów kodu [w pliku .editorconfig](../ide/editorconfig-code-style-settings-reference.md) lub na [edytora tekstów opcje](../ide/code-styles-and-quick-actions.md) strony, którą faktycznie konfigurujesz analizatorów Roslyn, które są wbudowane w program Visual Studio. Plików EditorConfig można również skonfigurować niektóre pakiety analizatora innych firm, takiego jak [analizatory FxCop analizujące kod](configure-fxcop-analyzers.md).

## <a name="editorconfig-versus-rule-sets"></a>Polecenia EditorConfig w porównaniu z zestawów reguł

**Q**: Należy skonfigurować Mój analizatory za pomocą zestawu reguł lub pliku .editorconfig?

**A**: Zestawy reguł i plików editorconfig są wzajemnie wykluczających się sposoby konfigurowania analizatorów. One może współistnieć. [Zestawów reguł](analyzer-rule-sets.md) pozwalają włączyć i wyłączyć reguły i ustawienia ich ważności. Plików EditorConfig oferują inne sposoby, aby skonfigurować reguły. Dla analizatory FxCop analizujące kod plików editorconfig pozwalają [definiujący typy kodu do analizy, które](fxcop-analyzer-options.md). Analizatory, które są wbudowane w program Visual Studio, aby uzyskać plików editorconfig pozwalają [definiowania stylów preferowanych kodu](../ide/editorconfig-code-style-settings-reference.md) dla kodu.

Oprócz zestawów reguł i plików editorconfig analizatory niektórych innych firm są skonfigurowane przy użyciu plików tekstowych, oznaczone jako [dodatkowe pliki](../ide/build-actions.md#build-action-values) dla C# i Kompilatory języka VB.

> [!NOTE]
> Plików EditorConfig nie można skonfigurować reguły analizy kodu statycznego, mogą zestawów reguł.

## <a name="analyzers-in-ci-builds"></a>Analizatory w kompilacjach ciągłej integracji

**Q**: Analizatory działają w kompilacjach ciągłej integracji (CI)?

**A**: Tak. Analizatory, które są instalowane z pakietu NuGet, te zasady są [wymuszane w czasie kompilacji](roslyn-analyzers-overview.md#build-errors), w tym podczas kompilacji ciągłej integracji. Analizatory używanych w konfiguracji reguły względem kompilacje ciągłej integracji z obu [zestawów reguł](analyzer-rule-sets.md) i [plików editorconfig](configure-fxcop-analyzers.md). Obecnie analizatorów kodu, które są wbudowane w program Visual Studio nie są dostępne jako pakiet NuGet, a więc te zasady nie są wykonalne w kompilację o ciągłej integracji.

## <a name="ide-analyzers-versus-stylecop"></a>Analizatory IDE i StyleCop

**Q**: Jaka jest różnica między analizatory StyleCop i analizatorów kodu programu Visual Studio IDE?

**A**: Środowiska IDE programu Visual Studio zawiera wbudowane analizatorów, które poszukują zarówno kod stylu i jakości w przypadku problemów. Te zasady pomagają korzystać z nowych funkcji języka, jak długo będą one wprowadzone i poprawić łatwości utrzymania kodu. Analizatory IDE są ciągle aktualizowane wraz z każdą wersją programu Visual Studio.

[Analizatory StyleCop](https://github.com/DotNetAnalyzers/StyleCopAnalyzers) są zainstalowane jako pakiet NuGet analizatory innych firm, które Sprawdzanie spójności stylu w kodzie. Ogólnie rzecz biorąc StyleCop reguły pozwalają na ustawienie preferencji dla kodu podstawowego nie wyróżniając jednego stylu zamiast innego.

## <a name="analyzers-versus-static-code-analysis"></a>Analizatory i statycznej analizy kodu

**Q**: Jaka jest różnica między analizatory i statycznej analizy kodu?

**A**: Analizatory analizę kodu źródłowego w czasie rzeczywistym i podczas kompilacji, natomiast statycznej analizy kodu, analizuje pliki binarne po zakończeniu kompilacji. Aby uzyskać więcej informacji, zobacz [analizatorów Roslyn a statycznej analizy kodu](roslyn-analyzers-overview.md#roslyn-analyzers-vs-static-code-analysis) i [analizatory FxCop analizujące kod często zadawane pytania dotyczące](fxcop-analyzers-faq.md).

## <a name="see-also"></a>Zobacz także

- [Omówienie analizatorów](roslyn-analyzers-overview.md)
- [.NET coding convention ustawienia dla wtyczki EditorConfig](../ide/editorconfig-code-style-settings-reference.md)