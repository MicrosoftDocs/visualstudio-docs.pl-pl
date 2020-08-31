---
title: Zainstaluj analizatory innych firm
ms.date: 08/27/2020
ms.topic: conceptual
helpviewer_keywords:
- code analysis, managed code
- analyzers
- Roslyn analyzers
author: mikadumont
ms.author: midumont
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 9da78f4c8e76f4e5b79f4cbdb0739d34fc465330
ms.sourcegitcommit: 016bcdc7cd3e3619457beb321800e98544efb6c9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/29/2020
ms.locfileid: "89091454"
---
# <a name="install-third-party-analyzers"></a>Zainstaluj analizatory innych firm

Program Visual Studio zawiera podstawowe zestawy .NET Compiler Platform (*Roslyn*) analizatorów. Te analizatory są zawsze włączone. Możesz zainstalować dodatkowe analizatory jako pakiety NuGet lub jako rozszerzenia programu Visual Studio w plikach *VSIX* .

## <a name="to-install-nuget-analyzer-packages"></a>Aby zainstalować pakiety analizatora NuGet

1. Znajdź pakiet analizatora, który chcesz zainstalować w systemie www.nuget.org.

   Na przykład możesz chcieć zainstalować [StyleCop. analizatory](https://www.nuget.org/packages/stylecop.analyzers/) , aby wyszukać problemy z stylem w bazie kodu.

2. Zainstaluj pakiet w programie Visual Studio przy użyciu [konsoli Menedżera pakietów](/nuget/quickstart/install-and-use-a-package-in-visual-studio#package-manager-console) lub [interfejsu użytkownika Menedżera pakietów](/nuget/quickstart/install-and-use-a-package-in-visual-studio#package-manager-console).

   > [!NOTE]
   > Strona www.nuget.org każdego pakietu analizatora pokazuje polecenie do wklejenia do **konsoli Menedżera pakietów**. Istnieje jeszcze przycisk przydatny do kopiowania tekstu do Schowka.

   Zestawy analizatora są zainstalowane i pojawiają się w **Eksplorator rozwiązań** w obszarze **References**  >  **analizatory**odwołań.

## <a name="to-install-vsix-analyzers"></a>Aby zainstalować analizatory VSIX

::: moniker range="vs-2017"

1. W programie Visual Studio wybierz pozycję **Narzędzia** > **rozszerzenia i aktualizacje**.

   Zostanie otwarte okno dialogowe **rozszerzenia i aktualizacje** .

   > [!NOTE]
   > Alternatywnie można znaleźć i pobrać rozszerzenie analizatora bezpośrednio z [Visual Studio Marketplace](https://marketplace.visualstudio.com).

::: moniker-end

::: moniker range=">=vs-2019"

1. W programie Visual Studio wybierz pozycję **rozszerzenia** > **Zarządzanie rozszerzeniami**.

   Zostanie otwarte okno dialogowe **Zarządzanie rozszerzeniami** .

   > [!NOTE]
   > Alternatywnie można znaleźć i pobrać rozszerzenie analizatora bezpośrednio z [Visual Studio Marketplace](https://marketplace.visualstudio.com).

::: moniker-end

2. W lewym okienku rozwiń pozycję **online** , a następnie wybierz pozycję **Visual Studio Marketplace**.

3. W polu wyszukiwania wpisz nazwę rozszerzenia analizatora, które chcesz zainstalować. Na przykład może być konieczne [zainstalowanie analizatorów FxCop firmy Microsoft](install-fxcop-analyzers.md#vsix) w celu sprawdzenia kodu pod kątem problemów z zabezpieczeniami i wydajnością, między innymi.

4. Wybierz pozycję **Pobierz**.

   Rozszerzenie jest pobierane.

5. Wybierz **przycisk OK** , aby zamknąć okno dialogowe, a następnie zamknij wszystkie wystąpienia programu Visual Studio, aby uruchomić **Instalatora VSIX**.

   Zostanie otwarte okno dialogowe **Instalator VSIX** .

   ![Instalator VSIX dla analizy kodu firmy Microsoft](media/vsix-installer-code-analysis.png)

6. Wybierz pozycję **Modyfikuj** , aby rozpocząć instalację.

7. Po minucie lub dwóch instalacjach zostanie zakończona. Wybierz pozycję **Zamknij**.

8. Otwórz ponownie program Visual Studio.

::: moniker range="vs-2017"

Jeśli chcesz sprawdzić, czy rozszerzenie jest zainstalowane, wybierz pozycję **Narzędzia**  >  **rozszerzenia i aktualizacje**. W oknie dialogowym **rozszerzenia i aktualizacje** wybierz **zainstalowaną** kategorię po lewej stronie, a następnie wyszukaj rozszerzenie według nazwy.

::: moniker-end

::: moniker range=">=vs-2019"

Jeśli chcesz sprawdzić, czy rozszerzenie jest zainstalowane, wybierz pozycję **rozszerzenia**  >  **Zarządzanie rozszerzeniami**. W oknie dialogowym **Zarządzanie rozszerzeniami** wybierz **zainstalowaną** kategorię po lewej stronie, a następnie wyszukaj rozszerzenie według nazwy.

::: moniker-end

## <a name="next-steps"></a>Następne kroki

> [!div class="nextstepaction"]
> [Korzystanie z analizatorów kodu w programie Visual Studio](../code-quality/use-roslyn-analyzers.md)

## <a name="see-also"></a>Zobacz też

- [Przegląd analizatorów kodu w programie Visual Studio](../code-quality/roslyn-analyzers-overview.md)
- [Instalowanie analizatorów FxCop](../code-quality/install-fxcop-analyzers.md)
