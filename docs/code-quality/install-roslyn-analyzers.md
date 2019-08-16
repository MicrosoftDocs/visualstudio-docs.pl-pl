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
ms.openlocfilehash: 284f33d9d7af885958ed13101e1449edc5c8f2be
ms.sourcegitcommit: 209ed0fcbb8daa1685e8d6b9a97f3857a4ce1152
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/16/2019
ms.locfileid: "69551089"
---
# <a name="install-net-compiler-platform-code-analyzers"></a>Zainstaluj .NET Compiler Platform analizatorów kodu

Program Visual Studio zawiera podstawowe zestawy .NET Compiler Platform (*Roslyn*) analizatorów. Te analizatory są zawsze włączone. Możesz zainstalować dodatkowe analizatory jako pakiety NuGet lub jako rozszerzenia programu Visual Studio w plikach *VSIX* .

## <a name="to-install-nuget-analyzer-packages"></a>Aby zainstalować pakiety analizatora NuGet

1. Znajdź pakiet analizatora, który chcesz zainstalować w systemie www.nuget.org.

   Na przykład może być konieczne [zainstalowanie analizatorów FxCop firmy Microsoft](install-fxcop-analyzers.md#to-install-fxcop-analyzers-as-a-nuget-package) w celu sprawdzenia kodu pod kątem problemów z zabezpieczeniami i wydajnością, między innymi. Lub zainstaluj [StyleCopAnalyzers](https://www.nuget.org/packages/stylecop.analyzers/) , aby wyszukać problemy z stylem w bazie kodu.

2. Zainstaluj pakiet w programie Visual Studio przy użyciu [konsoli Menedżera pakietów](/nuget/quickstart/install-and-use-a-package-in-visual-studio#package-manager-console) lub [interfejsu użytkownika Menedżera pakietów](/nuget/quickstart/install-and-use-a-package-in-visual-studio#package-manager-console).

   > [!NOTE]
   > Strona www.nuget.org każdego pakietu analizatora pokazuje polecenie do wklejenia do **konsoli Menedżera pakietów**. Istnieje jeszcze przycisk przydatny do kopiowania tekstu do Schowka.

   Zestawy analizatora są zainstalowane i pojawiają się w **Eksplorator rozwiązań** w obszarze analizatory **odwołań** > .

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

3. W polu wyszukiwania wpisz nazwę rozszerzenia analizatora, które chcesz zainstalować. Na przykład może być konieczne [zainstalowanie analizatorów FxCop firmy Microsoft](install-fxcop-analyzers.md#to-install-fxcop-analyzers-as-a-vsix) w celu sprawdzenia kodu pod kątem problemów z zabezpieczeniami i wydajnością, między innymi.

4. Wybierz pozycję **Pobierz**.

   Rozszerzenie jest pobierane.

5. Wybierz **przycisk OK** , aby zamknąć okno dialogowe, a następnie zamknij wszystkie wystąpienia programu Visual Studio, aby uruchomić **Instalatora VSIX**.

   Zostanie otwarte okno dialogowe **Instalator VSIX** .

   ![Instalator VSIX dla analizy kodu firmy Microsoft](media/vsix-installer-code-analysis.png)

6. Wybierz pozycję **Modyfikuj** , aby rozpocząć instalację.

7. Po minucie lub dwóch instalacjach zostanie zakończona. Wybierz pozycję **Zamknij**.

8. Otwórz ponownie program Visual Studio.

::: moniker range="vs-2017"

Jeśli chcesz sprawdzić, czy rozszerzenie jest zainstalowane, wybierz pozycję **Narzędzia** > **rozszerzenia i aktualizacje**. W oknie dialogowym **rozszerzenia i aktualizacje** wybierz zainstalowaną kategorię po lewej stronie, a następnie wyszukaj rozszerzenie według nazwy.

::: moniker-end

::: moniker range=">=vs-2019"

Jeśli chcesz sprawdzić, czy rozszerzenie jest zainstalowane, wybierz pozycję **rozszerzenia** > **Zarządzanie rozszerzeniami**. W oknie dialogowym **Zarządzanie rozszerzeniami** wybierz zainstalowaną kategorię po lewej stronie, a następnie wyszukaj rozszerzenie według nazwy.

::: moniker-end

## <a name="next-steps"></a>Następne kroki

> [!div class="nextstepaction"]
> [Korzystanie z analizatorów kodu w programie Visual Studio](../code-quality/use-roslyn-analyzers.md)

## <a name="see-also"></a>Zobacz także

- [Przegląd analizatorów kodu w programie Visual Studio](../code-quality/roslyn-analyzers-overview.md)
- [Zainstaluj analizatory FxCop](../code-quality/install-fxcop-analyzers.md)