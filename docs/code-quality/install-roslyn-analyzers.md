---
title: Zainstaluj analizatory innych firm
ms.date: 08/27/2020
description: Dowiedz się, jak instalować analizatory innych firm w programie Visual Studio. Zobacz jak zainstalować analizatory w plikach VSIX i pakietach analizatora NuGet.
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: 3c6978c19f01b278886f72ff21d62ebf6c5cf57f
ms.sourcegitcommit: 75bfdaab9a8b23a097c1e8538ed1cde404305974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/07/2020
ms.locfileid: "94348687"
---
# <a name="install-third-party-analyzers"></a>Instalowanie analizatorów innych firm

Program Visual Studio zawiera podstawowe zestawy .NET Compiler Platform ( *Roslyn* ) analizatorów. Te analizatory są zawsze włączone. Możesz zainstalować dodatkowe analizatory jako pakiety NuGet lub jako rozszerzenia programu Visual Studio w plikach *VSIX* .

## <a name="to-install-nuget-analyzer-packages"></a>Aby zainstalować pakiety analizatora NuGet

1. Znajdź pakiet analizatora, który chcesz zainstalować w systemie www.nuget.org.

   Na przykład możesz chcieć zainstalować [StyleCop. analizatory](https://www.nuget.org/packages/stylecop.analyzers/) , aby wyszukać problemy z stylem w bazie kodu.

2. Zainstaluj pakiet w programie Visual Studio przy użyciu [konsoli Menedżera pakietów](/nuget/quickstart/install-and-use-a-package-in-visual-studio#package-manager-console) lub [interfejsu użytkownika Menedżera pakietów](/nuget/quickstart/install-and-use-a-package-in-visual-studio#package-manager-console).

   > [!NOTE]
   > Strona www.nuget.org każdego pakietu analizatora pokazuje polecenie do wklejenia do **konsoli Menedżera pakietów**. Istnieje jeszcze przycisk przydatny do kopiowania tekstu do Schowka.

   Zestawy analizatora są zainstalowane i pojawiają się w **Eksplorator rozwiązań** w obszarze **References**  >  **analizatory** odwołań.

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

4. Kliknij pozycję **Pobierz**.

   Rozszerzenie jest pobierane.

5. Wybierz **przycisk OK** , aby zamknąć okno dialogowe, a następnie zamknij wszystkie wystąpienia programu Visual Studio, aby uruchomić **Instalatora VSIX**.

   Zostanie otwarte okno dialogowe **Instalator VSIX** .

   ![Instalator VSIX dla analizy kodu firmy Microsoft](media/vsix-installer-code-analysis.png)

6. Wybierz pozycję **Modyfikuj** , aby rozpocząć instalację.

7. Po minucie lub dwóch instalacjach zostanie zakończona. Wybierz pozycję **Close** (Zamknij).

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
