---
title: Pełnoekranowy i tryb obszaru wirtualnego
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- word wrap
- views, virtual space
- line numbers, displaying
- virtual space mode
- line numbers
- Code Editor, view and display options
- full screen mode
- Code Editor, modes
- views, splitting
- views, word wrapping
- fonts and size
- views, creating new windows
- views, line numbers
- views, changing mode
- views, outlining
ms.assetid: 1fb48027-d870-439f-8b72-4a0321390748
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: e5250176bee4993f9d01bffcaed71579c17e55c9
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/07/2018
ms.locfileid: "53056311"
---
# <a name="how-to-manage-editor-modes"></a>Porady: Zarządzanie trybami edytora

Edytor kodu programu Visual Studio można wyświetlić w różnych trybów wyświetlania.

> [!NOTE]
> Polecenia menu i okien dialogowych mogą różnić się od tych opisanych w tym artykule, w zależności od ustawień aktywnych lub wersji. Aby zmienić swoje ustawienia, na przykład aby **ogólne** lub **Visual C++** ustawienia, wybierz **narzędzia** > **Import i eksport ustawień**, a następnie wybierz **Resetuj wszystkie ustawienia**.

## <a name="enable-full-screen-mode"></a>Włącz tryb pełnoekranowy

Można wybrać ukryć wszystkie okna narzędzi i wyświetlić tylko okna dokumentu, należy włączyć **pełny ekran** trybu.

-   Naciśnij klawisz **Alt**+**Shift**+**Enter** do wprowadzania lub zamknąć **pełny ekran** trybu.

     --lub--

-   Należy wydać polecenie `View.Fullscreen` w **polecenia** okna.

## <a name="enable-virtual-space-mode"></a>Włącz tryb obszaru wirtualnego

W **wirtualną przestrzenią** tryb, spacje są dodawane na końcu każdego wiersza kodu. Wybierz tę opcję, aby umieść komentarze w momencie spójne obok kodu.

1.  Wybierz **opcje** z **narzędzia** menu.

2.  Rozwiń **edytora tekstów** folderu i wybierz polecenie **wszystkie języki** globalnie Ustaw tę opcję, lub wybierz folder, do określonego języka. Na przykład, aby włączyć numery wierszy tylko w języku Visual Basic, należy wybrać **podstawowe** > **edytora tekstów** węzła.

3.  Wybierz **ogólne** opcje, a następnie w obszarze **ustawienia**, wybierz opcję **włączyć wirtualną przestrzenią**.

    > [!NOTE]
    > **Wirtualna przestrzeń** jest włączone w **wybór kolumn** trybu. Gdy **wirtualną przestrzenią** nie jest włączony tryb punkt wstawiania przenoszony z końca jeden wiersz bezpośrednio do pierwszego znaku w następnym.

## <a name="see-also"></a>Zobacz także

- [Dopasowywanie edytora](../ide/customizing-the-editor.md)
- [Dostosowywanie układów okien w programie Visual Studio](../ide/customizing-window-layouts-in-visual-studio.md)
- [Czcionki i kolory, środowisko, okno dialogowe Opcje](../ide/reference/fonts-and-colors-environment-options-dialog-box.md)