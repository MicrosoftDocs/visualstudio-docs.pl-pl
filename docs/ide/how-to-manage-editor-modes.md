---
title: Pełny ekran i tryb przestrzeni wirtualnej
description: Dowiedz się, jak zarządzać trybami edytora programu Visual Studio, aby wyświetlić wszystkie narzędzia i okna w taki sposób, który najlepiej sprawdza się.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
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
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 112fbd727f28ce1dd3f72626c03e3cc6594da213
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99935895"
---
# <a name="how-to-manage-editor-modes"></a>Instrukcje: Zarządzanie trybami edytora

Edytor kodu programu Visual Studio można wyświetlić w różnych trybach wyświetlania.

> [!NOTE]
> Okna dialogowe i polecenia menu mogą się różnić od tych opisanych w tym artykule, w zależności od ustawień aktywnych lub wydania. Aby zmienić ustawienia, na przykład **Ogólne** lub **Visual C++** ustawienia, wybierz pozycję **Narzędzia**  >  **Importuj i Eksportuj ustawienia**, a następnie wybierz pozycję **Zresetuj wszystkie ustawienia**.

## <a name="enable-full-screen-mode"></a>Włącz tryb pełnoekranowy

Można ukryć wszystkie okna narzędzi i wyświetlić tylko okna dokumentów, **włączając tryb pełnoekranowy** .

- Naciśnij klawisze **Alt** + **SHIFT** + **Enter** , aby wejść lub wyjść z trybu **pełnoekranowego** .

     — lub —

- Wydaj polecenie `View.Fullscreen` w oknie **wiersza polecenia** .

## <a name="enable-virtual-space-mode"></a>Włącz tryb przestrzeni wirtualnej

W trybie **przestrzeni wirtualnej** spacje są wstawiane na końcu każdego wiersza kodu. Wybierz tę opcję, aby umieścić komentarze w spójnym punkcie obok kodu.

1. Wybierz **Opcje** z menu **Narzędzia** .

2. Rozwiń folder **Edytor tekstu** i wybierz **wszystkie języki** , aby ustawić tę opcję globalnie, lub wybierz określony folder języka. Aby na przykład włączyć numery wierszy tylko w Visual Basic, wybierz węzeł **podstawowy**  >  **Edytor tekstu** .

3. Wybierz opcje **Ogólne** i w obszarze **Ustawienia** wybierz pozycję **Włącz miejsce wirtualne**.

    > [!NOTE]
    > **Wirtualne miejsce** jest włączone w trybie **wyboru kolumny** . Gdy tryb **przestrzeni wirtualnej** nie jest włączony, punkt wstawiania przechodzi od końca jednego wiersza bezpośrednio do pierwszego znaku następnego.

## <a name="see-also"></a>Zobacz też

- [Dostosowywanie układów okien w programie Visual Studio](../ide/customizing-window-layouts-in-visual-studio.md)
- [Czcionki i kolory, środowisko, Opcje — okno dialogowe](../ide/reference/fonts-and-colors-environment-options-dialog-box.md)
