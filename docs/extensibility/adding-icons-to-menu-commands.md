---
title: Dodawanie ikon do poleceń menu | Microsoft Docs
description: Dowiedz się, jak dodać ikony do poleceń, które mogą być wyświetlane w menu i paskach narzędzi w zintegrowanym środowisku programistycznym (IDE) programu Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- icons [Visual Studio], adding to toolbars
- toolbars [Visual Studio], adding icons to commands
- commands [Visual Studio], adding icons
ms.assetid: 362a0c7e-5729-4297-a83f-1aba1a37fd44
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: eaf0a089c10c850c14b9ba2f807a69eada5d04b9
ms.sourcegitcommit: d6207a3a590c9ea84e3b25981d39933ad5f19ea3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/24/2020
ms.locfileid: "95597655"
---
# <a name="add-icons-to-menu-commands"></a>Dodawanie ikon do poleceń menu
Polecenia mogą znajdować się zarówno w menu, jak i na paskach narzędzi. Na paskach narzędzi wspólne polecenie jest wyświetlane z ikoną (aby zaoszczędzić miejsce) w menu, a polecenie zazwyczaj pojawia się zarówno w przypadku ikony, jak i tekstu.

 Ikony są 16 pikseli o szerokości do 16 pikseli i mogą mieć 8-bitową głębię kolorów (256 kolorów) lub 32-bitową głębię kolorów (True Color). 32-bitowe ikony kolorów są preferowane. Ikony są zwykle rozmieszczane w pojedynczym wierszu w pojedynczej mapie bitowej, chociaż wiele map bitowych jest dozwolonych. Ta mapa bitowa jest zadeklarowana w pliku *. vsct* wraz z poszczególnymi ikonami dostępnymi w mapie bitowej. Aby uzyskać więcej informacji, zobacz Dokumentacja [elementu mapy bitowe](../extensibility/bitmaps-element.md) .

## <a name="add-an-icon-to-a-command"></a>Dodawanie ikony do polecenia
 W poniższej procedurze przyjęto założenie, że masz istniejący projekt pakietu VSPackage z poleceniem menu. Aby dowiedzieć się, jak to zrobić, zobacz [Tworzenie rozszerzenia za pomocą polecenia menu](../extensibility/creating-an-extension-with-a-menu-command.md).

1. Utwórz mapę bitową z głębią kolorów 32-bitów. Ikona ma zawsze 16 x 16, więc ta mapa bitowa musi mieć 16 pikseli i mieć wielokrotność 16 pikseli.

     Każda ikona jest umieszczana na mapie bitowej obok siebie w pojedynczym wierszu. Użyj kanału alfa, aby wskazać miejsca przezroczystości w każdej ikonie.

     Jeśli używasz 8-bitowej głębi kolorów, użyj karmazynowego, `RGB(255,0,255)` jako przezroczystości. Jednak 32-bitowe ikony kolorów są preferowane.

2. Skopiuj plik ikony do katalogu *zasobów* w projekcie pakietu VSPackage. W **Eksplorator rozwiązań** Dodaj ikonę do projektu. (Wybierz **zasoby**, a następnie w menu kontekstowym kliknij przycisk **Dodaj**, a następnie **istniejący element** i wybierz plik ikony).

3. Otwórz plik *. vsct* w edytorze.

4. Dodaj `GuidSymbol` element o nazwie **testIcon**. Utwórz identyfikator GUID (**Narzędzia**  >  **Utwórz identyfikator GUID**, a następnie wybierz pozycję **Format rejestru** i kliknij przycisk **Kopiuj**) i wklej go do `value` atrybutu. Wynik powinien wyglądać następująco:

    ```xml
    <!-- Create your own GUID -->
    <GuidSymbol name="testIcon" value="{00000000-0000-0000-0000-0000}">
    ```

5. Dodaj `<IDSymbol>` do ikony. Ten `name` atrybut jest identyfikatorem ikony i `value` wskazuje jego pozycję na pasku, jeśli istnieje. Jeśli istnieje tylko jedna ikona, Dodaj 1. Wynik powinien wyglądać następująco:

    ```xml
    <!-- Create your own GUID -->
    <GuidSymbol name="testIcon" value="{00000000-0000-0000-0000-0000}">
        <IDSymbol name="testIcon1" value="1" />
    </GuidSymbol>
    ```

6. Utwórz `<Bitmap>` w `<Bitmaps>` sekcji pliku *. vsct* do reprezentowania mapy bitowej zawierającej ikony.

    - Ustaw `guid` wartość na nazwę `<GuidSymbol>` elementu, który został utworzony w poprzednim kroku.

    - Ustaw `href` wartość na ścieżkę względną pliku mapy bitowej (w tym przypadku **zasoby \\<ikony \> Nazwa pliku**.

    - Ustaw `usedList` wartość IDSymbol, która została utworzona wcześniej. Ten atrybut Określa rozdzielaną przecinkami listę ikon, które mają być używane w pakietu VSPackage. Ikony, które nie znajdują się na liście, są wykluczone.

         Blok mapy bitowej powinien wyglądać następująco:

        ```xml
        <Bitmap guid="testIcon" href="Resources\<icon file name>" usedList="testIcon1"/>
        ```

7. W istniejącym `<Button>` elemencie Ustaw `Icon` dla elementu wartości GUIDSymbol i IDSymbol utworzone wcześniej. Oto przykład elementu Button z tymi wartościami:

    ```xml
    <Button guid="guidAddIconCmdSet" id="cmdidMyCommand" priority="0x0100" type="Button">
        <Parent guid="guidAddIconCmdSet" id="MyMenuGroup" />
        <Icon guid="testIcon" id="testIcon1" />
        <Strings>
            <ButtonText>My Command name</ButtonText>
        </Strings>
    </Button>
    ```

8. Przetestuj ikonę. Skompiluj projekt i Rozpocznij debugowanie. W eksperymentalnym wystąpieniu Znajdź polecenie. Powinna zostać wyświetlona ikona, która została dodana.

## <a name="see-also"></a>Zobacz także
- [Rozszerzanie menu i poleceń](../extensibility/extending-menus-and-commands.md)
- [Dokumentacja schematu XML VSCT](../extensibility/vsct-xml-schema-reference.md)
