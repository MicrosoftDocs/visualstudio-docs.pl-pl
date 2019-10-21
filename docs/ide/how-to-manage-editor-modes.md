---
title: Pełny ekran i tryb przestrzeni wirtualnej
ms.date: 11/04/2016
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
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: fd3e238813c6cfd8674e5392d9ad20889e79c900
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72645852"
---
# <a name="how-to-manage-editor-modes"></a>Instrukcje: Zarządzanie trybami edytora

Edytor kodu programu Visual Studio można wyświetlić w różnych trybach wyświetlania.

> [!NOTE]
> Okna dialogowe i polecenia menu mogą się różnić od tych opisanych w tym artykule, w zależności od ustawień aktywnych lub wydania. Aby zmienić ustawienia, na przykład **Ogólne** lub ustawienia **wizualizacji C++**  , wybierz pozycję **Narzędzia** > **Ustawienia importu i eksportu**, a następnie wybierz pozycję **Zresetuj wszystkie ustawienia**.

## <a name="enable-full-screen-mode"></a>Włącz tryb pełnoekranowy

Można ukryć wszystkie okna narzędzi i wyświetlić tylko okna dokumentów, **włączając tryb pełnoekranowy** .

- Naciśnij klawisz **Alt** +**SHIFT** +**Enter** , aby wejść lub wyjść z trybu **pełnoekranowego** .

     --lub--

- Wydaj polecenie `View.Fullscreen` w oknie **poleceń** .

## <a name="enable-virtual-space-mode"></a>Włącz tryb przestrzeni wirtualnej

W trybie **przestrzeni wirtualnej** spacje są wstawiane na końcu każdego wiersza kodu. Wybierz tę opcję, aby umieścić komentarze w spójnym punkcie obok kodu.

1. Wybierz **Opcje** z menu **Narzędzia** .

2. Rozwiń folder **Edytor tekstu** i wybierz **wszystkie języki** , aby ustawić tę opcję globalnie, lub wybierz określony folder języka. Aby na przykład włączyć numery wierszy tylko w Visual Basic, wybierz węzeł**Edytor tekstu**  >  **podstawowa** .

3. Wybierz opcje **Ogólne** i w obszarze **Ustawienia**wybierz pozycję **Włącz miejsce wirtualne**.

    > [!NOTE]
    > **Wirtualne miejsce** jest włączone w trybie **wyboru kolumny** . Gdy tryb **przestrzeni wirtualnej** nie jest włączony, punkt wstawiania przechodzi od końca jednego wiersza bezpośrednio do pierwszego znaku następnego.

## <a name="see-also"></a>Zobacz także

- [Dostosowywanie układów okien w programie Visual Studio](../ide/customizing-window-layouts-in-visual-studio.md)
- [Czcionki i kolory, środowisko, Opcje — okno dialogowe](../ide/reference/fonts-and-colors-environment-options-dialog-box.md)