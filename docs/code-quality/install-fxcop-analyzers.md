---
title: Instalowanie analizatorów FxCop
ms.date: 08/03/2018
ms.topic: conceptual
helpviewer_keywords:
- fxcop analyzers
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: e4b97779c458fd7cb02ab5c168401f061869ccb1
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2019
ms.locfileid: "55953454"
---
# <a name="install-fxcop-analyzers-in-visual-studio"></a>Zainstaluj analizatory FxCop analizujące kod w programie Visual Studio

Firma Microsoft utworzyła zbiór analizatorów, o nazwie [Microsoft.CodeAnalysis.FxCopAnalyzers](https://www.nuget.org/packages/Microsoft.CodeAnalysis.FxCopAnalyzers), który zawiera najważniejsze reguły "FxCop" ze statycznej analizy kodu, przekonwertować analizatorów Roslyn. Te analizatory Sprawdź swój kod pod kątem bezpieczeństwa, wydajności i zagadnienia związane z projektowaniem, między innymi.

Te analizatory FxCop analizujące kod można zainstalować jako pakiet NuGet lub rozszerzeniu VSIX do programu Visual Studio. Aby dowiedzieć się więcej na temat zalet i wad każdego z nich, zobacz [vs pakietu NuGet. Rozszerzenie VSIX](roslyn-analyzers-overview.md#nuget-package-versus-vsix-extension).

## <a name="to-install-fxcop-analyzers-as-a-nuget-package"></a>Aby zainstalować analizatory FxCop analizujące kod jako pakiet NuGet

1. [Określić, która wersja pakietu analizatora](#fxcopanalyzers-package-versions) do zainstalowania, zależnie od wersji programu Visual Studio.

2. Zainstaluj pakiet w programie Visual Studio, za pomocą [Konsola Menedżera pakietów](/nuget/quickstart/install-and-use-a-package-in-visual-studio#package-manager-console) lub [interfejs użytkownika Menedżera pakietów](/nuget/quickstart/install-and-use-a-package-in-visual-studio#package-manager-console).

   > [!NOTE]
   > Na stronie nuget.org, dla każdego pakietu analizatora zawiera polecenia, aby wkleić w **Konsola Menedżera pakietów**. Jest parzysta przydatną przycisk, aby skopiować tekst do Schowka.
   >
   > ![Strona NuGet.org przedstawiający polecenia konsoli Menedżera pakietów](media/nuget-package-manager-command.png)

   Zestawy analizatora są instalowane i pojawiają się na **Eksploratora rozwiązań** w obszarze **odwołania** > **analizatory**.

   ![Węzeł analizatory w Eksploratorze rozwiązań](media/solution-explorer-analyzers-node.png)

### <a name="fxcopanalyzers-package-versions"></a>Wersje pakietów FxCopAnalyzers

Skorzystaj z poniższych wskazówek w celu określenia którą wersję pakiet analizatory FxCop analizujące kod w celu zainstalowania dla używanej wersji programu Visual Studio:

| Visual Studio w wersji | Wersja pakietu analizatora programu FxCop |
| - | - |
| Visual Studio 2017 w wersji 15.5 lub nowszej | 2.6.2 — przykład https://www.nuget.org/packages/Microsoft.CodeAnalysis.FxCopAnalyzers/2.6.2 |
| Visual Studio 2017 w wersji 15.3 lub 15.4 | 2.3.0-Beta1, na przykład https://www.nuget.org/packages/Microsoft.CodeAnalysis.FxCopAnalyzers/2.3.0-beta1 |
| Visual Studio 2017 wersja 15.0 — 15.2 | 2.0.0-Beta2, na przykład https://www.nuget.org/packages/Microsoft.CodeAnalysis.FxCopAnalyzers/2.0.0-beta2 |
| Visual Studio 2015 update 2 i 3 | 1.2.0-beta2 wersji, na przykład https://www.nuget.org/packages/Microsoft.CodeAnalysis.FxCopAnalyzers/1.2.0-beta2 |
| Visual Studio 2015 Update 1 | Wersji 1.1.0, na przykład https://www.nuget.org/packages/Microsoft.CodeAnalysis.FxCopAnalyzers/1.1. |
| Visual Studio 2015 RTW | W wersji 1.0.1, na przykład https://www.nuget.org/packages/Microsoft.CodeAnalysis.FxCopAnalyzers/1.0.1 |

## <a name="to-install-fxcop-analyzers-as-a-vsix"></a>Aby zainstalować analizatory FxCop analizujące kod jako VSIX

W programie Visual Studio 2017 w wersji 15.5 i nowszych można zainstalować [Microsoft Code Analysis 2017](https://marketplace.visualstudio.com/items?itemName=VisualStudioPlatformTeam.MicrosoftCodeAnalysis2017) rozszerzenia, który zawiera wszystkie analizatory FxCop analizujące kod dla projektów zarządzanych.

1. W programie Visual Studio, wybierz **narzędzia** > **rozszerzenia i aktualizacje**.

   **Rozszerzenia i aktualizacje** zostanie otwarte okno dialogowe.

   > [!NOTE]
   > Również pobrać rozszerzenia bezpośrednio z [Visual Studio Marketplace](https://marketplace.visualstudio.com/items?itemName=VisualStudioPlatformTeam.MicrosoftCodeAnalysis2017).

1. Rozwiń **Online** w okienku po lewej stronie, a następnie wybierz **Visual Studio Marketplace**.

1. W polu wyszukiwania wpisz "Analiza kodu" i poszukaj **Microsoft Code Analysis 2017** rozszerzenia.

   ![Rozszerzenia Microsoft analizy kodu](media/extensions-and-updates-code-analysis.png)

1. Wybierz **Pobierz**.

   Rozszerzenie zostanie pobrana.

1. Wybierz **OK** aby zamknąć okno dialogowe, a następnie zamknij wszystkie wystąpienia programu Visual Studio, aby uruchomić **Instalator VSIX**.

   **Instalator VSIX** zostanie otwarte okno dialogowe.

   ![Instalator VSIX dla analizy kodu firmy Microsoft](media/vsix-installer-code-analysis.png)

1. Wybierz **Modyfikuj** aby rozpocząć instalację.

1. Po minucie lub dwóch kończy instalację. Wybierz **Zamknij**.

1. Otwórz ponownie program Visual Studio.

Jeśli chcesz sprawdzić, czy rozszerzenie jest zainstalowane, wybierz opcję **narzędzia** > **rozszerzenia i aktualizacje**. W **rozszerzenia i aktualizacje** okno dialogowe, wybierz opcję **zainstalowane** kategorii po lewej stronie, a następnie Wyszukaj według nazwy rozszerzenia.

## <a name="see-also"></a>Zobacz także

- [Omówienie analizatorów Roslyn w programie Visual Studio](../code-quality/roslyn-analyzers-overview.md)
- [Używanie analizatorów Roslyn w programie Visual Studio](../code-quality/use-roslyn-analyzers.md)
- [Migracja z programu FxCop do analizatorów Roslyn](../code-quality/fxcop-analyzers.yml)