---
title: 'Instrukcje: Zarządzanie trybami edytora | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
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
caps.latest.revision: 24
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: a188e90d3feeb903eb8b4efceb91eb53cac3bdce
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72651849"
---
# <a name="how-to-manage-editor-modes"></a>Porady: zarządzanie trybami edytora
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Edytor Visual Studio Code można wyświetlić w różnych trybach wyświetlania.

> [!NOTE]
> Okna dialogowe i polecenia menu mogą się różnić od tych opisanych w Pomocy, w zależności od ustawień aktywnych lub wydania. Aby zmienić ustawienia, wybierz **Importuj i Eksportuj ustawienia** w menu **Narzędzia** . Aby uzyskać więcej informacji, zobacz [Dostosowywanie ustawień deweloperskich w programie Visual Studio](https://msdn.microsoft.com/22c4debb-4e31-47a8-8f19-16f328d7dcd3).

## <a name="enabling-full-screen-mode"></a>Włączanie trybu pełnoekranowego
 Można ukryć wszystkie okna narzędzi i wyświetlić tylko okna dokumentów, **włączając tryb pełnoekranowy** .

#### <a name="to-enable-full-screen-mode"></a>Aby włączyć tryb pełnoekranowy

- Naciśnij klawisze ALT + SHIFT + ENTER, aby wejść lub wyjść z trybu **pełnoekranowego** .

     --lub--

- Wydaj polecenie `View.Fullscreen` w oknie **poleceń** .

## <a name="enabling-virtual-space-mode"></a>Włączanie trybu przestrzeni wirtualnej
 W trybie **przestrzeni wirtualnej** spacje są wstawiane na końcu każdego wiersza kodu. Wybierz tę opcję, aby umieścić komentarze w spójnym punkcie obok kodu.

#### <a name="to-enable-virtual-space-mode"></a>Aby włączyć tryb przestrzeni wirtualnej

1. Wybierz **Opcje** z menu **Narzędzia** .

2. Rozwiń folder **Edytor tekstu** i wybierz **wszystkie języki** , aby ustawić tę opcję globalnie, lub wybierz określony folder języka. (Na przykład aby włączyć numery wierszy tylko w Visual Basic, wybierz opcje podstawowe, Edytor tekstu).

3. Wybierz opcje **Ogólne** i w obszarze **Ustawienia**wybierz pozycję **Włącz miejsce wirtualne**.

    > [!NOTE]
    > **Wirtualne miejsce** jest włączone w trybie **wyboru kolumny** . Gdy tryb **przestrzeni wirtualnej** nie jest włączony, punkt wstawiania przechodzi od końca jednego wiersza bezpośrednio do pierwszego znaku następnego.

## <a name="see-also"></a>Zobacz też
 [Dostosowanie edytora](../ide/customizing-the-editor.md) [How to: porządkowanie i dokowanie](../misc/how-to-arrange-and-dock-windows.md) [czcionek i kolorów systemu Windows, środowisko, Opcje — okno dialogowe](../ide/reference/fonts-and-colors-environment-options-dialog-box.md)
