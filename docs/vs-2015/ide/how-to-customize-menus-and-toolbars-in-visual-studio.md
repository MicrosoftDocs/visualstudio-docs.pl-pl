---
title: 'Instrukcje: Dostosowywanie menu i paski narzędzi'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
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
caps.latest.revision: 31
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 91223021ce6f05b91d47e7b7019fb0c5c02243db
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "63416790"
---
# <a name="how-to-customize-menus-and-toolbars-in-visual-studio"></a>Instrukcje: Dostosowywanie menu i pasków zadań w programie Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Można dostosować Visual Studio nie tylko przez dodawanie i usuwanie pasków narzędzi i menu na pasku menu, ale także przez dodawanie i usuwanie poleceń dowolnego danego paska narzędzi lub menu.

> [!WARNING]
> Po dostosowaniu paska narzędzi lub menu, upewnij się, że jego pole wyboru pozostaje wybrane w **Dostosuj** okno dialogowe. W przeciwnym razie zmiany nie są zachowywane po zamknięciu i ponownym otwarciu Visual Studio.

 **W tym temacie:**

- [Dodawanie, usuwanie lub przenoszenie menu na pasku menu](../ide/how-to-customize-menus-and-toolbars-in-visual-studio.md#bkmk_addmenu)

- [Dodawanie, usuwanie lub przenoszenie paska narzędzi](../ide/how-to-customize-menus-and-toolbars-in-visual-studio.md#bkmk_addtoolbar)

- [Dostosowywanie menu lub paska narzędzi](../ide/how-to-customize-menus-and-toolbars-in-visual-studio.md#bkmk_customize)

- [Resetowanie menu lub paska narzędzi](../ide/how-to-customize-menus-and-toolbars-in-visual-studio.md#bkmk_reset)

## <a name="bkmk_addmenu"></a> Dodawanie, usuwanie lub przenoszenie menu na pasku menu

1. Na pasku menu wybierz **narzędzia**, **Dostosuj**.

     **Dostosuj** zostanie otwarte okno dialogowe.

2. Na **polecenia** kartę, pozostaw **pasek Menu** wybrany przycisk opcji, należy pozostawić **pasek Menu** zaznaczony na liście obok tej opcji, a następnie wykonaj jedną z następujących zestawów kroki:

    - Aby dodać menu, wybierz opcję **Dodaj nowe Menu** przycisku, wybierz polecenie **Modyfikuj zaznaczenie** przycisk, a następnie nadaj nazwę menu, które chcesz dodać.

         ![Dostosuj — okno dialogowe, w którym pokazano, jak dodać menu](../ide/media/addmenu.png "DodajMenu")

    - Aby usunąć menu, wybierz je **kontrolki** , a następnie wybierz **Usuń** przycisku.

    - Aby przenieść menu na pasku menu, wybierz menu z **kontrolki** , a następnie wybierz **Przenieś w górę** lub **Przenieś w dół** przycisku.

## <a name="bkmk_addtoolbar"></a> Dodawanie, usuwanie lub przenoszenie paska narzędzi

1. Na pasku menu wybierz **narzędzia**, **Dostosuj**.

     **Dostosuj** zostanie otwarte okno dialogowe.

2. Na **narzędzi** karcie, wykonaj jedną z następujących zbiorów czynności:

    - Aby dodać pasek narzędzi, wybierz **New** przycisk, określ nazwę dla paska narzędzi, który chcesz dodać, a następnie wybierz **OK** przycisku.

         ![Dostosuj — okno dialogowe, w którym pokazano, jak dodać pasek narzędzi](../ide/media/addtoolbar.png "AddToolbar")

    - Aby usunąć niestandardowy pasek narzędzi, wybierz je **pasków narzędzi** , a następnie wybierz **Usuń** przycisku.

        > [!IMPORTANT]
        > Możesz usunąć paski narzędzi, które utworzyłeś, ale nie domyślne paski narzędzi.

    - Aby przenieść pasek narzędzi w inne miejsce dokowania, wybierz je **pasków narzędzi** wybierz **Modyfikuj zaznaczenie** przycisk, a następnie wybierz lokalizację na liście.

         Możesz również przeciągnąć pasek narzędzi za jego lewą krawędź, aby przenieść go w dowolne miejsce w głównym obszarze dokowania.

        > [!NOTE]
        > Aby uzyskać więcej informacji na temat sposobu zwiększania użyteczności i dostępności pasków narzędzi, zobacz [jak: Ustawianie opcji ułatwień dostępu IDE](../ide/reference/how-to-set-ide-accessibility-options.md).

## <a name="bkmk_customize"></a> Dostosowywanie menu lub paska narzędzi

1. Na pasku menu wybierz **narzędzia**, **Dostosuj**.

     **Dostosuj** zostanie otwarte okno dialogowe.

2. Na **polecenia** karty, wybierz przycisk opcji dla typu elementu, który chcesz dostosować.

3. Na liście dla tego typu elementu wybierz menu lub pasek narzędzi, który chcesz dostosować, a następnie wykonaj jeden z następujących zbiorów czynności:

    - Aby dodać polecenie, wybierz opcję **Dodaj polecenie** przycisku.

         W **Dodaj polecenie** okna dialogowego pole, wybierz element na liście **kategorie** listy, wybierz element na liście **polecenia** , a następnie wybierz **OK**przycisku.

         ![Dodaj okno dialogowe polecenia w programie Visual Studio](../ide/media/addcommand.png "funkcji AddCommand")

    - Aby usunąć polecenie, wybierz je **kontrolki** , a następnie wybierz **Usuń** przycisku.

    - Aby zmienić kolejność poleceń, wybierz polecenie na liście **kontrolki** , a następnie wybierz **Przenieś w górę** lub **Przenieś w dół** przycisku.

    - Aby podzielić polecenia w grupy, wybierz polecenie na liście **kontrolki** wybierz **Modyfikuj zaznaczenie** przycisk, a następnie wybierz **Rozpocznij grupę** w wyświetlonym menu.

## <a name="bkmk_reset"></a> Resetowanie menu lub paska narzędzi

1. Na pasku menu wybierz **narzędzia**, **Dostosuj**.

     **Dostosuj** zostanie otwarte okno dialogowe.

2. Na **polecenia** karty, wybierz przycisk opcji dla typu elementu, który chcesz zresetować.

3. Na liście dla tego typu elementu wybierz menu lub pasek narzędzi, który chcesz zresetować.

4. Wybierz **Modyfikuj zaznaczenie** przycisk, a następnie wybierz **resetowania** w wyświetlonym menu.

     Możesz także zresetować wszystkie menu i paski narzędzi, wybierając **Resetuj wszystko** przycisku.
