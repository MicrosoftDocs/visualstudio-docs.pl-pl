---
title: Dostosowywanie menu i pasków narzędzi
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.renametoolbar
- vs.customize.toolbars
- vs.buttoneditor
- vs.customize.commands
- vs.newtoolbar
helpviewer_keywords:
- captions, customizing toolbar
- custom toolbars [Visual Studio]
- command buttons, customizing toolbar
- labels, customizing toolbar
- images [Visual Studio], toolbar buttons
- buttons [Visual Studio], custom toolbars
- toolbars [Visual Studio], creating in the IDE
- icons [Visual Studio], customizing toolbar
- commands [Visual Studio], customizing environment
- customizing toolbars
- toolbars [Visual Studio], customizing
- toolbars [Visual Studio], customizing in the IDE
ms.assetid: b570ae2f-5302-45dc-9cc9-8d4d1ad50603
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: ed425b120d5d47fb684294ce17bd7d48374c638e
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "79301854"
---
# <a name="how-to-customize-menus-and-toolbars-in-visual-studio"></a>Jak: Dostosowywanie menu i pasków narzędzi w programie Visual Studio

Program Visual Studio można dostosować nie tylko przez dodanie i usunięcie pasków narzędzi i menu na pasku menu, ale także przez dodanie i usunięcie poleceń na danym pasku narzędzi lub menu.

> [!WARNING]
> Po dostosowaniu paska narzędzi lub menu upewnij się, że jego pole wyboru pozostaje zaznaczone w oknie dialogowym **Dostosowywanie.** W przeciwnym razie zmiany nie są zachowywane po zamknięciu i ponownym otwarciu Visual Studio.

## <a name="add-remove-or-move-a-menu-on-the-menu-bar"></a>Dodawanie, usuwanie lub przenoszenie menu na pasku menu

1. Na pasku menu wybierz pozycję **Narzędzia** > **Dostosowywanie**.

     Zostanie otwarte okno dialogowe **Dostosowywanie.**

2. Na karcie **Polecenia** pozostaw zaznaczony przycisk opcji **Pasek menu,** pozostaw pasek **menu** zaznaczony na liście obok tej opcji, a następnie wykonaj jeden z następujących zestawów kroków:

    - Aby dodać menu, wybierz przycisk **Dodaj nowe menu,** wybierz przycisk **Modyfikuj zaznaczenie,** a następnie nazwij menu, które chcesz dodać.

        ![Okno dialogowe Dostosowywanie przedstawiające dodawanie menu](../ide/media/addmenu.png)

    - Aby usunąć menu, wybierz je na liście **Formanty,** a następnie wybierz przycisk **Usuń.**

    - Aby przenieść menu na pasku menu, wybierz menu na liście **Formanty,** a następnie wybierz przycisk Przenieś w **górę** lub **Przenieś w dół.**

## <a name="add-remove-or-move-a-toolbar"></a>Dodawanie, usuwanie lub przenoszenie paska narzędzi

1. Na pasku menu wybierz pozycję **Narzędzia** > **Dostosowywanie**.

     Zostanie otwarte okno dialogowe **Dostosowywanie.**

2. Na karcie **Pasek narzędzi** wykonaj jeden z następujących zestawów kroków:

    - Aby dodać pasek narzędzi, wybierz przycisk **Nowy,** określ nazwę paska narzędzi, który chcesz dodać, a następnie wybierz przycisk **OK.**

        ![Okno dialogowe Dostosowywanie przedstawiające dodawanie paska narzędzi](../ide/media/addtoolbar.png)

    - Aby usunąć niestandardowy pasek narzędzi, wybierz go na liście **Paski narzędzi,** a następnie wybierz przycisk **Usuń.**

        > [!IMPORTANT]
        > Możesz usunąć paski narzędzi, które utworzyłeś, ale nie domyślne paski narzędzi.

    - Aby przenieść pasek narzędzi do innej lokalizacji dokowania, wybierz go na liście **Paski narzędzi,** wybierz przycisk **Modyfikuj zaznaczenie,** a następnie wybierz lokalizację na wyświetlona liście.

        Możesz również przeciągnąć pasek narzędzi za jego lewą krawędź, aby przenieść go w dowolne miejsce w głównym obszarze dokowania.

        > [!NOTE]
        > Aby uzyskać więcej informacji na temat poprawy użyteczności i dostępności pasków narzędzi, zobacz [Jak: Ustawianie opcji ułatwień dostępu IDE](../ide/reference/how-to-set-ide-accessibility-options.md).

## <a name=""></a><a name="customizing_menu">Dostosowywanie menu lub paska narzędzi</a>

1. Na pasku menu wybierz pozycję **Narzędzia** > **Dostosowywanie**.

    Zostanie otwarte okno dialogowe **Dostosowywanie.**

2. Na karcie **Polecenia** wybierz przycisk opcji dla typu elementu, który chcesz dostosować.

3. Na liście dla tego typu elementu wybierz menu lub pasek narzędzi, który chcesz dostosować, a następnie wykonaj jeden z następujących zbiorów czynności:

    - Aby dodać polecenie, wybierz przycisk **Dodaj polecenie.**

        W oknie dialogowym **Dodawanie polecenia** wybierz element z listy **Kategorie,** wybierz element na liście **Polecenia,** a następnie wybierz przycisk **OK.**

        ![Okno dialogowe Dodawanie polecenia w programie Visual Studio](../ide/media/addcommand.png)

    - Aby usunąć polecenie, wybierz je na liście **Formanty,** a następnie wybierz przycisk **Usuń.**

    - Aby zamiesz było zamiesz według kolejności, wybierz polecenie na liście **Formanty,** a następnie wybierz przycisk Przenieś w **górę** lub **Przenieś w dół.**

    - Aby grupować polecenia pod linią poziomą, wybierz pierwsze polecenie na liście **Formanty,** wybierz przycisk **Modyfikuj zaznaczenie,** a następnie wybierz polecenie **Rozpocznij grupę** w wyświetlonym menu.

## <a name="reset-a-menu-or-a-toolbar"></a>Resetowanie menu lub paska narzędzi

1. Na pasku menu wybierz pozycję **Narzędzia** > **Dostosowywanie**.

    Zostanie otwarte okno dialogowe **Dostosowywanie.**

2. Na karcie **Polecenia** wybierz przycisk opcji dla typu elementu, który chcesz zresetować.

3. Na liście dla tego typu elementu wybierz menu lub pasek narzędzi, który chcesz zresetować.

4. Wybierz przycisk **Modyfikuj zaznaczenie,** a następnie wybierz polecenie **Resetuj** w wyświetlonym menu.

    Można również zresetować wszystkie menu i paski narzędzi, wybierając przycisk **Resetuj wszystko.**

## <a name="see-also"></a>Zobacz też

- [Personalizowanie ide](../ide/personalizing-the-visual-studio-ide.md)
- [Dopasowywanie edytora](../ide/how-to-change-text-case-in-the-editor.md)
