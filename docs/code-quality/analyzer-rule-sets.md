---
title: Zestawy reguł analizatora
ms.date: 04/22/2019
ms.topic: conceptual
helpviewer_keywords:
- analyzers, rule sets
- rule sets for analyzers
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 32ed328cb399f0cd3e9a2a147d29fad56b845399
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "63387699"
---
# <a name="rule-sets-for-roslyn-analyzers"></a>Zestawy reguł na potrzeby analizatorów Roslyn

Zestawy wstępnie zdefiniowanych reguł są dołączane do niektórych pakietów analizatora NuGet. Na przykład zestawy reguł, które są dołączone [Microsoft.CodeAnalysis.FxCopAnalyzers](https://www.nuget.org/packages/Microsoft.CodeAnalysis.FxCopAnalyzers/) pakiet analizatora NuGet (począwszy od wersji 2.6.2) Włącz lub Wyłącz zasady na podstawie ich kategorii, takie jak zabezpieczenia, nazw, lub wydajność. Korzystanie z zestawów reguł można łatwo szybko wyświetlić tylko te naruszenia reguły, które odnoszą się do określonej kategorii reguły.

W przypadku migrowania ze starszego "FxCop" statycznej analizy kodu do analizatorów Roslyn, te zestawy reguł umożliwiają kontynuowanie przy użyciu tej samej konfiguracji reguły, wcześniej używane.

## <a name="use-analyzer-rule-sets"></a>Korzystanie z zestawów reguł analizatora

Po zakończeniu [zainstaluj pakiet analizatora NuGet](install-roslyn-analyzers.md), zlokalizuj wstępnie zdefiniowany zestaw reguł jego *zestawów reguł* katalogu. Na przykład, jeśli odwołujesz `Microsoft.CodeAnalysis.FxCopAnalyzers` analizatora pakietów, a następnie można znaleźć jego katalog zestawów reguł w *% USERPROFILE %\\.nuget\packages\microsoft.codeanalysis.fxcopanalyzers\\\<wersji \>\rulesets*. Z tego miejsca możesz można przeciągnij i upuść, lub skopiuj i Wklej, co najmniej jeden z zestawów reguł do projektu programu Visual Studio w **Eksploratora rozwiązań**.

Aby aktywny zestaw reguł dla analizy zestaw reguł, kliknij prawym przyciskiem myszy projekt w **Eksploratora rozwiązań** i wybierz polecenie **właściwości**. Na stronach właściwości projektu, wybierz **analizy kodu** kartę. W obszarze **Uruchom ten zestaw reguł**, wybierz opcję **Przeglądaj**, a następnie wybierz odpowiednią regułę zestaw, który został skopiowany do katalogu projektu. Teraz widoczne tylko naruszeń zasady dla tych reguł, które są włączone w wybranym zestawem reguł.

Możesz również [Dostosuj zestaw wstępnie zdefiniowanych reguł](how-to-create-a-custom-rule-set.md#create-a-custom-rule-set) zgodnie z preferencjami. Na przykład zmienić ważność co najmniej jedną regułę tak, aby naruszeń są traktowane jako błędy lub ostrzeżenia w **lista błędów**.

## <a name="available-rule-sets"></a>Zestawy reguł dostępne

Analizator wstępnie zdefiniowane zestawy reguł obejmują trzy zestawów reguł, które wpływają na wszystkie reguły w pakiecie&mdash;taki, który umożliwia ich wszystkich, taki, który wyłącza je wszystkie, a drugie honoruje każdej reguły domyślne ważności i włączenie ustawienia:

- AllRulesEnabled.ruleset
- AllRulesDisabled.ruleset
- AllRulesDefault.ruleset

Ponadto istnieją dwa zestawy reguł dla każdej kategorii reguły w pakiecie, takich jak wydajność czy zabezpieczeń. Jeden zestaw reguł włącza wszystkie reguły dla kategorii, a jeden zestaw reguł honoruje ważność i włączenie wartości domyślne dla każdej reguły w kategorii.

[Microsoft.CodeAnalysis.FxCopAnalyzers](https://www.nuget.org/packages/Microsoft.CodeAnalysis.FxCopAnalyzers/) pakiet analizatora NuGet obejmuje zestawy reguł w ramach następujących kategorii, które dopasowanie zestawów reguł na dostępne dla starszej wersji "FxCop" statycznej analizy kodu:

- projekt
- dokumentacja
- utrzymanie
- nazewnictwo
- wydajność
- niezawodność
- zabezpieczenia
- wykorzystanie

## <a name="see-also"></a>Zobacz także

- [Analizatory — często zadawane pytania](analyzers-faq.md)
- [Omówienie analizatory platformie kompilatora .NET](roslyn-analyzers-overview.md)
- [Instalowanie analizatorów](install-roslyn-analyzers.md)
- [Użyj analizatorów](use-roslyn-analyzers.md)
- [Używanie zestawów reguł do grupowania reguł analizy kodu](using-rule-sets-to-group-code-analysis-rules.md)
