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
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 84c4b2e5aa532becc1bf9bc50a3c7bcdbd2b8d4e
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2019
ms.locfileid: "55955638"
---
# <a name="how-to-customize-menus-and-toolbars-in-visual-studio"></a>Instrukcje: Dostosowywanie menu i pasków zadań w programie Visual Studio

Można dostosować Visual Studio, nie tylko przez dodawanie i usuwanie pasków narzędzi i menu na pasku menu, ale także przez dodawanie i usuwanie poleceń dowolnego danego paska narzędzi lub menu.

> [!WARNING]
> Po dostosowaniu paska narzędzi lub menu, upewnij się, że jego pole wyboru pozostaje wybrane w **Dostosuj** okno dialogowe. W przeciwnym razie zmiany nie są zachowywane po zamknięciu i ponownym otwarciu Visual Studio.

## <a name="add-remove-or-move-a-menu-on-the-menu-bar"></a>Dodawanie, usuwanie lub przenoszenie menu na pasku menu

1.  Na pasku menu wybierz **narzędzia** > **Dostosuj**.

     **Dostosuj** zostanie otwarte okno dialogowe.

2.  Na **polecenia** kartę, pozostaw **pasek Menu** wybrany przycisk opcji, należy pozostawić **pasek Menu** zaznaczony na liście obok tej opcji, a następnie wykonaj jedną z następujących zestawów kroki:

    -   Aby dodać menu, wybierz opcję **Dodaj nowe Menu** przycisku, wybierz polecenie **Modyfikuj zaznaczenie** przycisk, a następnie nadaj nazwę menu, które chcesz dodać.

        ![Dostosuj — okno dialogowe, w którym pokazano, jak dodać menu](../ide/media/addmenu.png)

    -   Aby usunąć menu, wybierz je **kontrolki** , a następnie wybierz **Usuń** przycisku.

    -   Aby przenieść menu na pasku menu, wybierz menu z **kontrolki** , a następnie wybierz **Przenieś w górę** lub **Przenieś w dół** przycisku.

## <a name="add-remove-or-move-a-toolbar"></a>Dodawanie, usuwanie lub przenoszenie paska narzędzi

1.  Na pasku menu wybierz **narzędzia** > **Dostosuj**.

     **Dostosuj** zostanie otwarte okno dialogowe.

2.  Na **narzędzi** karcie, wykonaj jedną z następujących zbiorów czynności:

    -   Aby dodać pasek narzędzi, wybierz **New** przycisk, określ nazwę dla paska narzędzi, który chcesz dodać, a następnie wybierz **OK** przycisku.

        ![Dostosuj — okno dialogowe, w którym pokazano, jak dodać pasek narzędzi](../ide/media/addtoolbar.png)

    -   Aby usunąć niestandardowy pasek narzędzi, wybierz je **pasków narzędzi** , a następnie wybierz **Usuń** przycisku.

        > [!IMPORTANT]
        > Możesz usunąć paski narzędzi, które utworzyłeś, ale nie domyślne paski narzędzi.

    -   Aby przenieść pasek narzędzi w inne miejsce dokowania, wybierz je **pasków narzędzi** wybierz **Modyfikuj zaznaczenie** przycisk, a następnie wybierz lokalizację na liście.

        Możesz również przeciągnąć pasek narzędzi za jego lewą krawędź, aby przenieść go w dowolne miejsce w głównym obszarze dokowania.

        > [!NOTE]
        > Aby uzyskać więcej informacji na temat sposobu zwiększania użyteczności i dostępności pasków narzędzi, zobacz [jak: Ustawianie opcji ułatwień dostępu IDE](../ide/reference/how-to-set-ide-accessibility-options.md).

## <a name="customizing_menu">Dostosowywanie menu lub paska narzędzi</a>

1.  Na pasku menu wybierz **narzędzia** > **Dostosuj**.

    **Dostosuj** zostanie otwarte okno dialogowe.

2.  Na **polecenia** karty, wybierz przycisk opcji dla typu elementu, który chcesz dostosować.

3.  Na liście dla tego typu elementu wybierz menu lub pasek narzędzi, który chcesz dostosować, a następnie wykonaj jeden z następujących zbiorów czynności:

    -   Aby dodać polecenie, wybierz opcję **Dodaj polecenie** przycisku.

        W **Dodaj polecenie** okna dialogowego pole, wybierz element na liście **kategorie** listy, wybierz element na liście **polecenia** , a następnie wybierz **OK**przycisku.

        ![Dodaj okno dialogowe polecenia w programie Visual Studio](../ide/media/addcommand.png)

    -   Aby usunąć polecenie, wybierz je **kontrolki** , a następnie wybierz **Usuń** przycisku.

    -   Aby zmienić kolejność poleceń, wybierz polecenie na liście **kontrolki** , a następnie wybierz **Przenieś w górę** lub **Przenieś w dół** przycisku.

    -   Do grupy poleceń w linii poziomej, wybierz pierwsze polecenie w **kontrolki** wybierz **Modyfikuj zaznaczenie** przycisk, a następnie wybierz **Rozpocznij grupę** w wyświetlonego menu.

## <a name="reset-a-menu-or-a-toolbar"></a>Resetowanie menu lub paska narzędzi

1.  Na pasku menu wybierz **narzędzia** > **Dostosuj**.

    **Dostosuj** zostanie otwarte okno dialogowe.

2.  Na **polecenia** karty, wybierz przycisk opcji dla typu elementu, który chcesz zresetować.

3.  Na liście dla tego typu elementu wybierz menu lub pasek narzędzi, który chcesz zresetować.

4.  Wybierz **Modyfikuj zaznaczenie** przycisk, a następnie wybierz **resetowania** w wyświetlonym menu.

    Możesz także zresetować wszystkie menu i paski narzędzi, wybierając **Resetuj wszystko** przycisku.

## <a name="see-also"></a>Zobacz także

- [Personalizowanie środowiska IDE](../ide/personalizing-the-visual-studio-ide.md)
- [Dopasowywanie edytora](../ide/customizing-the-editor.md)