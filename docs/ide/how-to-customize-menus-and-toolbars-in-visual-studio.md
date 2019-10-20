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
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: f5dc68374193c90fe248f92005a266a658f3f668
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72656082"
---
# <a name="how-to-customize-menus-and-toolbars-in-visual-studio"></a>Instrukcje: Dostosowywanie menu i pasków narzędzi w programie Visual Studio

Program Visual Studio można dostosować nie tylko przez dodawanie i Usuwanie pasków narzędzi i menu na pasku menu, ale również przez dodawanie i usuwanie poleceń z dowolnego danego paska narzędzi lub menu.

> [!WARNING]
> Po dostosowaniu paska narzędzi lub menu upewnij się, że pole wyboru pozostaje zaznaczone w oknie dialogowym **Dostosowywanie** . W przeciwnym razie zmiany nie są zachowywane po zamknięciu i ponownym otwarciu Visual Studio.

## <a name="add-remove-or-move-a-menu-on-the-menu-bar"></a>Dodawanie, usuwanie lub przenoszenie menu na pasku menu

1. Na pasku menu wybierz kolejno opcje **narzędzia**  > **Dostosuj**.

     Zostanie otwarte okno dialogowe **Dostosuj** .

2. Na karcie **polecenia** pozostaw wybrany przycisk opcji **pasek menu** , pozostaw **pasek menu** zaznaczony na liście obok tej opcji, a następnie wykonaj jeden z następujących zestawów czynności:

    - Aby dodać menu, wybierz przycisk **Dodaj nowe menu** , wybierz przycisk **Modyfikuj wybór** , a następnie nadaj nazwę menu, które chcesz dodać.

        ![Dostosowywanie okna dialogowego przedstawiającego sposób dodawania menu](../ide/media/addmenu.png)

    - Aby usunąć menu, wybierz je z listy **formanty** , a następnie wybierz przycisk **Usuń** .

    - Aby przenieść menu na pasku menu, wybierz menu na liście **kontrolki** , a następnie wybierz przycisk **Przenieś w górę** lub **Przenieś w dół** .

## <a name="add-remove-or-move-a-toolbar"></a>Dodawanie, usuwanie lub przenoszenie paska narzędzi

1. Na pasku menu wybierz kolejno opcje **narzędzia**  > **Dostosuj**.

     Zostanie otwarte okno dialogowe **Dostosuj** .

2. Na karcie **pasek narzędzi** wykonaj jeden z następujących zestawów czynności:

    - Aby dodać pasek narzędzi, wybierz przycisk **Nowy** , określ nazwę paska narzędzi, który chcesz dodać, a następnie wybierz przycisk **OK** .

        ![Dostosuj okno dialogowe pokazujące, jak dodać pasek narzędzi](../ide/media/addtoolbar.png)

    - Aby usunąć niestandardowy pasek narzędzi, wybierz go na liście **paski narzędzi** , a następnie wybierz przycisk **Usuń** .

        > [!IMPORTANT]
        > Możesz usunąć paski narzędzi, które utworzyłeś, ale nie domyślne paski narzędzi.

    - Aby przenieść pasek narzędzi do innej lokalizacji dokowania, wybierz ją na liście **paski narzędzi** , wybierz przycisk **Modyfikuj wybór** , a następnie wybierz lokalizację na wyświetlonej liście.

        Możesz również przeciągnąć pasek narzędzi za jego lewą krawędź, aby przenieść go w dowolne miejsce w głównym obszarze dokowania.

        > [!NOTE]
        > Aby uzyskać więcej informacji na temat zwiększania użyteczności i dostępności pasków narzędzi, zobacz [How to: Set opcje ułatwienia dostępu IDE](../ide/reference/how-to-set-ide-accessibility-options.md).

## <a name="customizing_menu">Dostosowywanie menu lub paska narzędzi</a>

1. Na pasku menu wybierz kolejno opcje **narzędzia**  > **Dostosuj**.

    Zostanie otwarte okno dialogowe **Dostosuj** .

2. Na karcie **polecenia** , wybierz przycisk opcji dla typu elementu, który chcesz dostosować.

3. Na liście dla tego typu elementu wybierz menu lub pasek narzędzi, który chcesz dostosować, a następnie wykonaj jeden z następujących zbiorów czynności:

    - Aby dodać polecenie, kliknij przycisk **Dodaj polecenie** .

        W oknie dialogowym **Dodawanie polecenia** wybierz element na liście **Kategorie** , wybierz element na liście **polecenia** , a następnie wybierz przycisk **OK** .

        ![Okno dialogowe Dodawanie polecenia w programie Visual Studio](../ide/media/addcommand.png)

    - Aby usunąć polecenie, wybierz je z listy **formanty** , a następnie wybierz przycisk **Usuń** .

    - Aby zmienić kolejność poleceń, wybierz polecenie na liście **kontrolki** , a następnie wybierz przycisk **Przenieś w górę** lub **Przenieś w dół** .

    - Aby zgrupować polecenia w ramach linii poziomej, wybierz pierwsze polecenie z listy **kontrolki** , wybierz przycisk **Modyfikuj wybór** , a następnie w wyświetlonym menu wybierz polecenie **Rozpocznij grupę** .

## <a name="reset-a-menu-or-a-toolbar"></a>Resetowanie menu lub paska narzędzi

1. Na pasku menu wybierz kolejno opcje **narzędzia**  > **Dostosuj**.

    Zostanie otwarte okno dialogowe **Dostosuj** .

2. Na karcie **polecenia** , wybierz przycisk opcji dla typu elementu, który chcesz zresetować.

3. Na liście dla tego typu elementu wybierz menu lub pasek narzędzi, który chcesz zresetować.

4. Wybierz przycisk **Modyfikuj wybór** , a następnie w wyświetlonym menu wybierz polecenie **Zresetuj** .

    Możesz również zresetować wszystkie menu i paski narzędzi, wybierając przycisk **Resetuj wszystko** .

## <a name="see-also"></a>Zobacz także

- [Personalizowanie środowiska IDE](../ide/personalizing-the-visual-studio-ide.md)
- [Dopasowywanie edytora](../ide/how-to-change-text-case-in-the-editor.md)