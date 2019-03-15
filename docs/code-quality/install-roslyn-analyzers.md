---
title: Instalowanie analizatorów Roslyn
ms.date: 08/03/2018
ms.topic: conceptual
helpviewer_keywords:
- code analysis, managed code
- analyzers
- Roslyn analyzers
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 2b1859d422b0f3a76947a64e754521efcda46e65
ms.sourcegitcommit: 4ffb7be5384ad566ce46538032bf8561754c61a4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2019
ms.locfileid: "57982938"
---
# <a name="install-net-compiler-platform-analyzers"></a>Instalowanie analizatorów platformie kompilatora .NET

Program Visual Studio zawiera podstawowy zestaw platformy kompilatora .NET (*Roslyn*) analizatorów. Te analizatory są zawsze włączone. Można zainstalować dodatkowe analizatory jako pakietów NuGet lub jako rozszerzenia programu Visual Studio w *VSIX* plików.

## <a name="to-install-nuget-analyzer-packages"></a>Aby zainstalować pakiety analizatora NuGet

1. Znajdź pakiet analizatora, które chcesz zainstalować na www.nuget.org. Na przykład możesz chcieć [zainstalować analizatory Microsoft FxCop](install-fxcop-analyzers.md#to-install-fxcop-analyzers-as-a-nuget-package) Aby sprawdzić swój kod pod kątem problemów zabezpieczeń i wydajności, między innymi.

2. Zainstaluj pakiet w programie Visual Studio, za pomocą [Konsola Menedżera pakietów](/nuget/quickstart/install-and-use-a-package-in-visual-studio#package-manager-console) lub [interfejs użytkownika Menedżera pakietów](/nuget/quickstart/install-and-use-a-package-in-visual-studio#package-manager-console).

   > [!NOTE]
   > Strona www.nuget.org dla każdego pakietu analizatora zawiera polecenia, aby wkleić w **Konsola Menedżera pakietów**. Jest parzysta przydatną przycisk, aby skopiować tekst do Schowka.
   >
   > ![Strona NuGet.org przedstawiający polecenia konsoli Menedżera pakietów](media/nuget-install-command.png)

   Zestawy analizatora są zainstalowane i są wyświetlane w **Eksploratora rozwiązań** w obszarze **odwołania** > **analizatory**.

## <a name="to-install-vsix-analyzers"></a>Aby zainstalować VSIX analizatorów

::: moniker range="vs-2017"

1. W programie Visual Studio, wybierz **narzędzia** > **rozszerzenia i aktualizacje**.

   **Rozszerzenia i aktualizacje** zostanie otwarte okno dialogowe.

   > [!NOTE]
   > Alternatywnie można znaleźć i pobrać rozszerzenia analizatora bezpośrednio z [Visual Studio Marketplace](https://marketplace.visualstudio.com).

::: moniker-end

::: moniker range=">=vs-2019"

1. W programie Visual Studio, wybierz **rozszerzenia** > **Zarządzaj rozszerzeniami**.

   **Zarządzaj rozszerzeniami** zostanie otwarte okno dialogowe.

   > [!NOTE]
   > Alternatywnie można znaleźć i pobrać rozszerzenia analizatora bezpośrednio z [Visual Studio Marketplace](https://marketplace.visualstudio.com).

::: moniker-end

2. Rozwiń **Online** w okienku po lewej stronie, a następnie wybierz **Visual Studio Marketplace**.

3. W polu wyszukiwania wpisz nazwę rozszerzenia analizatora, które chcesz zainstalować. Na przykład możesz chcieć [zainstalować analizatory Microsoft FxCop](install-fxcop-analyzers.md#to-install-fxcop-analyzers-as-a-vsix) Aby sprawdzić swój kod pod kątem problemów zabezpieczeń i wydajności, między innymi.

4. Wybierz **Pobierz**.

   Rozszerzenie zostanie pobrana.

5. Wybierz **OK** aby zamknąć okno dialogowe, a następnie zamknij wszystkie wystąpienia programu Visual Studio, aby uruchomić **Instalator VSIX**.

   **Instalator VSIX** zostanie otwarte okno dialogowe.

   ![Instalator VSIX dla analizy kodu firmy Microsoft](media/vsix-installer-code-analysis.png)

6. Wybierz **Modyfikuj** aby rozpocząć instalację.

7. Po minucie lub dwóch kończy instalację. Wybierz **Zamknij**.

8. Otwórz ponownie program Visual Studio.

::: moniker range="vs-2017"

Jeśli chcesz sprawdzić, czy rozszerzenie jest zainstalowane, wybierz opcję **narzędzia** > **rozszerzenia i aktualizacje**. W **rozszerzenia i aktualizacje** okno dialogowe, wybierz opcję **zainstalowane** kategorii po lewej stronie, a następnie Wyszukaj według nazwy rozszerzenia.

::: moniker-end

::: moniker range=">=vs-2019"

Jeśli chcesz sprawdzić, czy rozszerzenie jest zainstalowane, wybierz opcję **rozszerzenia** > **Zarządzaj rozszerzeniami**. W **Zarządzaj rozszerzeniami** okno dialogowe, wybierz opcję **zainstalowane** kategorii po lewej stronie, a następnie Wyszukaj według nazwy rozszerzenia.

::: moniker-end

## <a name="next-steps"></a>Następne kroki

> [!div class="nextstepaction"]
> [Używanie analizatorów Roslyn w programie Visual Studio](../code-quality/use-roslyn-analyzers.md)

## <a name="see-also"></a>Zobacz także

- [Omówienie analizatorów Roslyn w programie Visual Studio](../code-quality/roslyn-analyzers-overview.md)
- [Zainstaluj analizatory FxCop analizujące kod](../code-quality/install-fxcop-analyzers.md)