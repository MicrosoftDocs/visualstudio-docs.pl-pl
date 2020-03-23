---
title: Instalowanie analizatorów FxCop
ms.date: 08/03/2018
ms.topic: conceptual
helpviewer_keywords:
- fxcop analyzers
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 1d734ea4d87dc5d1b8f2ca7f1a1891a4cf7d512b
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "79508774"
---
# <a name="install-fxcop-analyzers-in-visual-studio"></a>Instalowanie analizatorów FxCop w programie Visual Studio

Microsoft stworzył zestaw analizatorów, o nazwie [Microsoft.CodeAnalysis.FxCopAnalyzers](https://www.nuget.org/packages/Microsoft.CodeAnalysis.FxCopAnalyzers), który zawiera najważniejsze reguły "FxCop" z starszej analizy. Te analizatory sprawdzić kod pod kątem zabezpieczeń, wydajności i projektowania problemów, między innymi.

Można zainstalować te analizatory FxCop jako pakiet NuGet lub jako rozszerzenie VSIX do programu Visual Studio. Aby dowiedzieć się więcej o zaletach i wadach każdego z nich, zobacz [Pakiet NuGet vs. ROZSZERZENIE VSIX](roslyn-analyzers-overview.md#nuget-package-versus-vsix-extension).

## <a name="nuget-package"></a>Pakiet NuGet

::: moniker range=">=vs-2019"

W programie Visual Studio 2019 w wersji 16.3 lub nowszej można zainstalować pakiet [Microsoft.CodeAnalysis.FxCopAnalyzers](https://www.nuget.org/packages/Microsoft.CodeAnalysis.FxCopAnalyzers) NuGet bezpośrednio ze strony właściwości analizy kodu projektu:

1. Kliknij prawym przyciskiem myszy węzeł projektu w **Eksploratorze rozwiązań**, wybierz **polecenie Właściwości**, a następnie wybierz kartę **Analiza kodu.**

   ![Instalowanie pakietu analizatorów FxCop ze strony właściwości w programie Visual Studio](media/install-fxcop-properties-page.png)

2. Wybierz pozycję **Zainstaluj**.

   Visual Studio instaluje najnowszą wersję pakietu Microsoft.CodeAnalysis.FxCopAnalyzers. Zestawy pojawiają się w **Eksploratorze rozwiązań**  > w obszarze **Analizatory odwołań**.**Analyzers**

   ![Węzeł analizatorów w Eksploratorze rozwiązań](media/solution-explorer-analyzers-node.png)

Jeśli używasz starszej wersji programu Visual Studio 2019, zainstaluj pakiet przy użyciu [konsoli Menedżera pakietów](/nuget/quickstart/install-and-use-a-package-in-visual-studio#package-manager-console) lub interfejsu [użytkownika Menedżera pakietów.](/nuget/quickstart/install-and-use-a-package-in-visual-studio#package-manager-console)

::: moniker-end

::: moniker range="vs-2017"

1. [Określ, która wersja pakietu analizatora](#fxcopanalyzers-package-versions) do zainstalowania, na podstawie wersji programu Visual Studio.

2. Zainstaluj pakiet w programie Visual Studio przy użyciu [konsoli Menedżera pakietów](/nuget/quickstart/install-and-use-a-package-in-visual-studio#package-manager-console) lub interfejsu [użytkownika Menedżera pakietów](/nuget/quickstart/install-and-use-a-package-in-visual-studio#package-manager-console).

   > [!NOTE]
   > Strona nuget.org dla każdego pakietu analizatora pokazuje polecenie wklejenia do **konsoli Menedżera pakietów**. Istnieje nawet przydatny przycisk, aby skopiować tekst do schowka.
   >
   > ![strona NuGet.org z poleceniem Konsoli Menedżera pakietów](media/nuget-package-manager-command.png)

   Zestawy analizatora są zainstalowane i pojawiają się w **Eksploratorze rozwiązań** w obszarze **Analizatory** > **odwołań**.

::: moniker-end

### <a name="custom-installation"></a>Instalacja niestandardowa

W przypadku instalacji niestandardowej, na przykład w celu określenia innej wersji pakietu, wybierz przycisk wielokropek (...) na stronie właściwości analizy kodu projektu. Ten przycisk otwiera menedżera pakietów NuGet z "Microsoft.CodeAnalysis.FxCopAnalyzers" jako ciąg wyszukiwania.

![Instalowanie niestandardowego pakietu analizatorów FxCop ze strony właściwości w programie Visual Studio](media/install-fxcop-properties-page-ellipsis.png)

> [!TIP]
> [Określ, która wersja pakietu analizatora](#fxcopanalyzers-package-versions) do zainstalowania, na podstawie wersji programu Visual Studio. Pakiet można również zainstalować z interfejsu [użytkownika Menedżera pakietów](/nuget/quickstart/install-and-use-a-package-in-visual-studio#package-manager-console).

### <a name="fxcopanalyzers-package-versions"></a>Wersje pakietów FxCopAnalyzers

Użyj następujących wskazówek, aby określić, która wersja pakietu analizatorów FxCop do zainstalowania dla wersji programu Visual Studio:

| Wersja programu Visual Studio | Wersja pakietu analizatora FxCop |
| - | - |
| Visual Studio 2019 (wszystkie wersje)<br />Visual Studio 2017 w wersji 15.8 i nowszej | [najnowsza](https://www.nuget.org/packages/Microsoft.CodeAnalysis.FxCopAnalyzers/) |
| Visual Studio 2017 w wersji od 15.5 do 15.7 | [2.6.3](https://www.nuget.org/packages/Microsoft.CodeAnalysis.FxCopAnalyzers/2.6.3) |
| Visual Studio 2017 w wersji 15.3 do 15.4 | [2.3.0-beta1](https://www.nuget.org/packages/Microsoft.CodeAnalysis.FxCopAnalyzers/2.3.0-beta1) |
| Visual Studio 2017 w wersji 15.0 do 15.2 | [2.0.0-beta2](https://www.nuget.org/packages/Microsoft.CodeAnalysis.FxCopAnalyzers/2.0.0-beta2) |
| Aktualizacja programu Visual Studio 2015 2 i 3 | [1.2.0-beta2](https://www.nuget.org/packages/Microsoft.CodeAnalysis.FxCopAnalyzers/1.2.0-beta2) |
| Visual Studio 2015 Update 1 | [1.1.0](https://www.nuget.org/packages/Microsoft.CodeAnalysis.FxCopAnalyzers/1.1.0) |
| Visual Studio 2015 RTW | [1.0.1](https://www.nuget.org/packages/Microsoft.CodeAnalysis.FxCopAnalyzers/1.0.1) |

## <a name="vsix"></a>Vsix

::: moniker range="vs-2017"

W programie Visual Studio 2017 w wersji 15.5 lub nowszej można zainstalować rozszerzenie [Microsoft Code Analysis 2017,](https://marketplace.visualstudio.com/items?itemName=VisualStudioPlatformTeam.MicrosoftCodeAnalysis2017) które zawiera wszystkie analizatory FxCop dla zarządzanych projektów.

1. W programie Visual Studio wybierz pozycję **Rozszerzenia i aktualizacje** **narzędzi** > .

   Zostanie otwarte okno dialogowe **Rozszerzenia i aktualizacje.**

   > [!NOTE]
   > Alternatywnie pobierz rozszerzenie bezpośrednio z [programu Visual Studio Marketplace](https://marketplace.visualstudio.com/items?itemName=VisualStudioPlatformTeam.MicrosoftCodeAnalysis2017).

2. Rozwiń pozycję **Online** w lewym okienku, a następnie wybierz pozycję **Visual Studio Marketplace**.

3. W polu wyszukiwania wpisz "analiza kodu" i poszukaj rozszerzenia **Microsoft Code Analysis 2017.**

   ![Rozszerzenie Microsoft Code Analysis 2017](media/extensions-and-updates-code-analysis.png)

::: moniker-end

::: moniker range=">=vs-2019"

Rozszerzenie [Microsoft Code Analysis 2019](https://marketplace.visualstudio.com/items?itemName=VisualStudioPlatformTeam.MicrosoftCodeAnalysis2019) zawiera wszystkie analizatory FxCop dla zarządzanych projektów. Aby zainstalować to rozszerzenie:

1. W programie Visual Studio wybierz pozycję **Rozszerzenia** > **zarządzaj rozszerzeniami**.

   Zostanie otwarte okno dialogowe **Zarządzanie rozszerzeniami.**

   > [!NOTE]
   > Alternatywnie pobierz rozszerzenie bezpośrednio z [programu Visual Studio Marketplace](https://marketplace.visualstudio.com/items?itemName=VisualStudioPlatformTeam.MicrosoftCodeAnalysis2019).

2. Rozwiń pozycję **Online** w lewym okienku, a następnie wybierz pozycję **Visual Studio Marketplace**.

3. W polu wyszukiwania wpisz "analiza kodu" i poszukaj rozszerzenia **Microsoft Code Analysis 2019.**

   ![Rozszerzenie Microsoft Code Analysis 2019](media/manage-extensions-code-analysis.png)

::: moniker-end

4. Wybierz przycisk **Download** (Pobierz).

   Rozszerzenie zostanie pobrane.

5. Wybierz **przycisk OK,** aby zamknąć okno dialogowe, a następnie zamknij wszystkie wystąpienia programu Visual Studio, aby uruchomić **Instalatora VSIX**.

   Zostanie otwarte okno dialogowe **Instalatora VSIX.**

   ::: moniker range="vs-2017"

   ![Instalator VSIX dla analizy kodu firmy Microsoft](media/vsix-installer-code-analysis.png)

   ::: moniker-end

6. Wybierz **opcję Modyfikuj,** aby rozpocząć instalację.

   Po minucie lub dwóch instalacja zostanie zakończona.

7. Wybierz **pozycję Zamknij**, a następnie ponownie otwórz program Visual Studio.

::: moniker range="vs-2017"

Jeśli chcesz sprawdzić, czy rozszerzenie jest zainstalowane, wybierz opcję**Rozszerzenia i aktualizacje** **narzędzi** > . W oknie dialogowym **Rozszerzenia i aktualizacje** wybierz kategorię **Zainstalowane** po lewej stronie, a następnie wyszukaj rozszerzenie według nazwy.

::: moniker-end

::: moniker range=">=vs-2019"

Jeśli chcesz sprawdzić, czy rozszerzenie jest zainstalowane, wybierz **opcję Rozszerzenia** > **Zarządzaj rozszerzeniami**. W oknie dialogowym **Zarządzanie rozszerzeniami** wybierz kategorię **Zainstalowane** po lewej stronie, a następnie wyszukaj rozszerzenie według nazwy.

::: moniker-end

## <a name="see-also"></a>Zobacz też

- [Omówienie analizatorów kodu w programie Visual Studio](../code-quality/roslyn-analyzers-overview.md)
- [Używanie analizatorów kodu w programie Visual Studio](../code-quality/use-roslyn-analyzers.md)
- [Migrowanie z starszej analizy do analizatorów kodu](../code-quality/migrate-from-legacy-analysis-to-fxcop-analyzers.md)
