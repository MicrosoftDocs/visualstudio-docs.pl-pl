---
title: Instalowanie analizatorów FxCop
ms.date: 08/03/2018
ms.topic: how-to
helpviewer_keywords:
- fxcop analyzers
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: df9d345e8557f10d764dce6e56c7491d2c026747
ms.sourcegitcommit: 0d3d157949b539c78bc101a3c3b456bbcb5af7de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/17/2020
ms.locfileid: "88286656"
---
# <a name="install-fxcop-analyzers-in-visual-studio"></a>Zainstaluj analizatory FxCop w programie Visual Studio

Firma Microsoft utworzyła zestaw analizatorów o nazwie [Microsoft. CodeAnalysis. FxCopAnalyzers](https://www.nuget.org/packages/Microsoft.CodeAnalysis.FxCopAnalyzers), który zawiera najważniejsze reguły "FxCop" ze starszej analizy. Analizatory te sprawdzają kod pod kątem bezpieczeństwa, wydajności i problemów projektowych między innymi.

Można zainstalować te analizatory FxCop jako pakiet NuGet lub rozszerzenie VSIX do programu Visual Studio. Aby dowiedzieć się więcej o zaletach i wadach każdego z nich, zobacz [rozszerzenie pakietu NuGet a VSIX](roslyn-analyzers-overview.md#nuget-package-versus-vsix-extension).

## <a name="nuget-package"></a>Pakiet NuGet

::: moniker range=">=vs-2019"

W programie Visual Studio 2019 w wersji 16,3 lub nowszej można zainstalować pakiet NuGet [Microsoft. CodeAnalysis. FxCopAnalyzers](https://www.nuget.org/packages/Microsoft.CodeAnalysis.FxCopAnalyzers) bezpośrednio na stronie właściwości analizy kodu projektu:

1. Kliknij prawym przyciskiem myszy węzeł projektu w **Eksplorator rozwiązań**, wybierz polecenie **Właściwości**, a następnie wybierz kartę **Analiza kodu** .

   ![Zainstaluj pakiet analizatorów FxCop na stronie właściwości w programie Visual Studio](media/install-fxcop-properties-page.png)

2. Wybierz pozycję **Zainstaluj**.

   Program Visual Studio instaluje najnowszą wersję pakietu Microsoft. CodeAnalysis. FxCopAnalyzers. Zestawy pojawiają się w **Eksplorator rozwiązań** w obszarze **References**  >  **analizatory**odwołań.

   ![Węzeł analizatorów w Eksplorator rozwiązań](media/solution-explorer-analyzers-node.png)

Jeśli używasz starszej wersji programu Visual Studio 2019, zainstaluj pakiet przy użyciu [konsoli Menedżera pakietów](/nuget/quickstart/install-and-use-a-package-in-visual-studio#package-manager-console) lub [interfejsu użytkownika Menedżera pakietów](/nuget/quickstart/install-and-use-a-package-in-visual-studio#package-manager-console).

::: moniker-end

::: moniker range="vs-2017"

1. [Określ wersję pakietu analizatora](#fxcopanalyzers-package-versions) do zainstalowania na podstawie używanej wersji programu Visual Studio.

2. Zainstaluj pakiet w programie Visual Studio przy użyciu [konsoli Menedżera pakietów](/nuget/quickstart/install-and-use-a-package-in-visual-studio#package-manager-console) lub [interfejsu użytkownika Menedżera pakietów](/nuget/quickstart/install-and-use-a-package-in-visual-studio#package-manager-console).

   > [!NOTE]
   > Strona nuget.org każdego pakietu analizatora pokazuje polecenie do wklejenia do **konsoli Menedżera pakietów**. Istnieje jeszcze przycisk przydatny do kopiowania tekstu do Schowka.
   >
   > ![Strona NuGet.org przedstawiająca polecenie konsoli Menedżera pakietów](media/nuget-package-manager-command.png)

   Zestawy analizatora są zainstalowane i pojawiają się w **Eksplorator rozwiązań** w **References** obszarze > **analizatory**odwołań.

::: moniker-end

### <a name="custom-installation"></a>Instalacja niestandardowa

W przypadku instalacji niestandardowej, na przykład w celu określenia innej wersji pakietu, wybierz przycisk wielokropka (...) na stronie właściwości analizy kodu projektu. Ten przycisk otwiera Menedżera pakietów NuGet przy użyciu "Microsoft. CodeAnalysis. FxCopAnalyzers" jako ciągu wyszukiwania.

![Instalowanie niestandardowego pakietu analizatorów FxCop ze strony właściwości w programie Visual Studio](media/install-fxcop-properties-page-ellipsis.png)

> [!TIP]
> Określ [wersję pakietu analizatora](#fxcopanalyzers-package-versions) do zainstalowania na podstawie używanej wersji programu Visual Studio. Możesz również zainstalować pakiet z poziomu [interfejsu użytkownika Menedżera pakietów](/nuget/quickstart/install-and-use-a-package-in-visual-studio#package-manager-console).

### <a name="fxcopanalyzers-package-versions"></a>Wersje pakietów FxCopAnalyzers

Skorzystaj z poniższych wskazówek, aby określić, która wersja pakietu analizatorów FxCop ma zostać zainstalowana dla używanej wersji programu Visual Studio:

| Wersja programu Visual Studio | Wersja pakietu analizatora FxCop |
| - | - |
| Visual Studio 2019 (wszystkie wersje) | [Ostatnia](https://www.nuget.org/packages/Microsoft.CodeAnalysis.FxCopAnalyzers/) | 
| Visual Studio 2017 w wersji 15,9 | [2.9.10](https://www.nuget.org/packages/Microsoft.CodeAnalysis.FxCopAnalyzers/2.9.10) |
| Program Visual Studio 2017 w wersji 15,5 do 15,8 | [2.6.4](https://www.nuget.org/packages/Microsoft.CodeAnalysis.FxCopAnalyzers/2.6.4) |
| Program Visual Studio 2017 w wersji 15,3 do 15,4 | [2.3.0 — beta1](https://www.nuget.org/packages/Microsoft.CodeAnalysis.FxCopAnalyzers/2.3.0-beta1) |
| Program Visual Studio 2017 w wersji 15,0 do 15,2 | [2.0.0 — beta2](https://www.nuget.org/packages/Microsoft.CodeAnalysis.FxCopAnalyzers/2.0.0-beta2) |
| Visual Studio 2015 Update 2 i 3 | [1.2.0 — beta2](https://www.nuget.org/packages/Microsoft.CodeAnalysis.FxCopAnalyzers/1.2.0-beta2) |
| Visual Studio 2015 Update 1 | [1.1.0](https://www.nuget.org/packages/Microsoft.CodeAnalysis.FxCopAnalyzers/1.1.0) |
| RTW programu Visual Studio 2015 | [1.0.1](https://www.nuget.org/packages/Microsoft.CodeAnalysis.FxCopAnalyzers/1.0.1) |

## <a name="vsix"></a>VSIX

::: moniker range="vs-2017"

W programie Visual Studio 2017 w wersji 15,5 lub nowszej można zainstalować rozszerzenie [Microsoft Code Analysis 2017](https://marketplace.visualstudio.com/items?itemName=VisualStudioPlatformTeam.MicrosoftCodeAnalysis2017) , które zawiera wszystkie analizatory FxCop dla projektów zarządzanych.

1. W programie Visual Studio wybierz pozycję **Narzędzia** > **rozszerzenia i aktualizacje**.

   Zostanie otwarte okno dialogowe **rozszerzenia i aktualizacje** .

   > [!NOTE]
   > Alternatywnie możesz pobrać rozszerzenie bezpośrednio z [Visual Studio Marketplace](https://marketplace.visualstudio.com/items?itemName=VisualStudioPlatformTeam.MicrosoftCodeAnalysis2017).

2. W lewym okienku rozwiń pozycję **online** , a następnie wybierz pozycję **Visual Studio Marketplace**.

3. W polu wyszukiwania wpisz ciąg "Analiza kodu" i Wyszukaj rozszerzenie **Microsoft Code analysis 2017** .

   ![Rozszerzenie Microsoft Code Analysis 2017](media/extensions-and-updates-code-analysis.png)

::: moniker-end

::: moniker range=">=vs-2019"

Rozszerzenie [Microsoft Code Analysis 2019](https://marketplace.visualstudio.com/items?itemName=VisualStudioPlatformTeam.MicrosoftCodeAnalysis2019) zawiera wszystkie analizatory FxCop dla projektów zarządzanych. Aby zainstalować to rozszerzenie:

1. W programie Visual Studio wybierz pozycję **rozszerzenia** > **Zarządzanie rozszerzeniami**.

   Zostanie otwarte okno dialogowe **Zarządzanie rozszerzeniami** .

   > [!NOTE]
   > Alternatywnie możesz pobrać rozszerzenie bezpośrednio z [Visual Studio Marketplace](https://marketplace.visualstudio.com/items?itemName=VisualStudioPlatformTeam.MicrosoftCodeAnalysis2019).

2. W lewym okienku rozwiń pozycję **online** , a następnie wybierz pozycję **Visual Studio Marketplace**.

3. W polu wyszukiwania wpisz ciąg "Analiza kodu" i Wyszukaj rozszerzenie **Microsoft Code analysis 2019** .

   ![Rozszerzenie Microsoft Code Analysis 2019](media/manage-extensions-code-analysis.png)

::: moniker-end

4. Kliknij pozycję **Pobierz**.

   Rozszerzenie jest pobierane.

5. Wybierz **przycisk OK** , aby zamknąć okno dialogowe, a następnie zamknij wszystkie wystąpienia programu Visual Studio, aby uruchomić **Instalatora VSIX**.

   Zostanie otwarte okno dialogowe **Instalator VSIX** .

   ::: moniker range="vs-2017"

   ![Instalator VSIX dla analizy kodu firmy Microsoft](media/vsix-installer-code-analysis.png)

   ::: moniker-end

6. Wybierz pozycję **Modyfikuj** , aby rozpocząć instalację.

   Po minucie lub dwóch instalacjach zostanie zakończona.

7. Wybierz pozycję **Zamknij**, a następnie ponownie otwórz program Visual Studio.

::: moniker range="vs-2017"

Jeśli chcesz sprawdzić, czy rozszerzenie jest zainstalowane, wybierz pozycję **Narzędzia**  >  **rozszerzenia i aktualizacje**. W oknie dialogowym **rozszerzenia i aktualizacje** wybierz **zainstalowaną** kategorię po lewej stronie, a następnie wyszukaj rozszerzenie według nazwy.

::: moniker-end

::: moniker range=">=vs-2019"

Jeśli chcesz sprawdzić, czy rozszerzenie jest zainstalowane, wybierz pozycję **rozszerzenia**  >  **Zarządzanie rozszerzeniami**. W oknie dialogowym **Zarządzanie rozszerzeniami** wybierz **zainstalowaną** kategorię po lewej stronie, a następnie wyszukaj rozszerzenie według nazwy.

::: moniker-end

## <a name="see-also"></a>Zobacz też

- [Przegląd analizatorów kodu w programie Visual Studio](../code-quality/roslyn-analyzers-overview.md)
- [Korzystanie z analizatorów kodu w programie Visual Studio](../code-quality/use-roslyn-analyzers.md)
- [Migrowanie ze starszej wersji analizy do analizatorów kodu](../code-quality/migrate-from-legacy-analysis-to-fxcop-analyzers.md)
