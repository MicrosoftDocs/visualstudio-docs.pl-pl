---
title: Tryb pełnoekranowy i wirtualna przestrzeń
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
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 77f224a6e3a1b12ed17799ddf6a2fc5c23f5d4cc
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "75591037"
---
# <a name="how-to-manage-editor-modes"></a>Jak: Zarządzanie trybami edytora

Edytor kodu programu Visual Studio można wyświetlić w różnych trybach wyświetlania.

> [!NOTE]
> Okna dialogowe i polecenia menu, które widzisz, mogą różnić się od tych opisanych w tym artykule w zależności od aktywnych ustawień lub wersji. Aby zmienić ustawienia, na przykład na **Ustawienia ogólne** lub **Visual C++,** wybierz pozycję Ustawienia**importu i eksportu** **narzędzi,** > a następnie wybierz pozycję **Resetuj wszystkie ustawienia**.

## <a name="enable-full-screen-mode"></a>Włącz tryb pełnoekranowy

Można ukryć wszystkie okna narzędzi i wyświetlić tylko okna dokumentu, włączając tryb **pełnoekranowy.**

- Naciśnij **klawisz Alt**+**Shift**+**Enter,** aby wejść lub wyjść z trybu **pełnoekranowego.**

     — lub —

- Wydaj `View.Fullscreen` polecenie w oknie **Polecenia.**

## <a name="enable-virtual-space-mode"></a>Włącz tryb przestrzeni wirtualnej

W trybie **przestrzeni wirtualnej** spacje są wstawiane na końcu każdego wiersza kodu. Wybierz tę opcję, aby umieścić komentarze w spójnym punkcie obok kodu.

1. Z menu **Narzędzia** wybierz **polecenie Opcje.**

2. Rozwiń folder **Edytor tekstu** i wybierz pozycję **Wszystkie języki,** aby ustawić tę opcję globalnie, lub wybierz określony folder języka. Na przykład, aby włączyć numery wierszy tylko w języku Visual Basic, wybierz węzeł**Edytor tekstu** **podstawowego.** > 

3. Wybierz opcje **ogólne** i w obszarze **Ustawienia**wybierz pozycję **Włącz przestrzeń wirtualną**.

    > [!NOTE]
    > **Przestrzeń wirtualna** jest włączona w trybie **wyboru kolumny.** Gdy tryb **przestrzeni wirtualnej** nie jest włączony, punkt wstawiania przesuwa się od końca jednego wiersza bezpośrednio do pierwszego znaku następnego.

## <a name="see-also"></a>Zobacz też

- [Dostosowywanie układów okien w programie Visual Studio](../ide/customizing-window-layouts-in-visual-studio.md)
- [Okna dialogowe Czcionki i kolory, Środowisko, Opcje](../ide/reference/fonts-and-colors-environment-options-dialog-box.md)
