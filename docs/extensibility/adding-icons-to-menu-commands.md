---
title: Dodawanie ikon do poleceń Menu | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- icons [Visual Studio], adding to toolbars
- toolbars [Visual Studio], adding icons to commands
- commands [Visual Studio], adding icons
ms.assetid: 362a0c7e-5729-4297-a83f-1aba1a37fd44
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: d1c54ee6b448e5830b478f10029a0d2d958e7699
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/29/2019
ms.locfileid: "66352365"
---
# <a name="add-icons-to-menu-commands"></a>Dodawanie ikon do poleceń menu
Polecenia może znajdować się w menu i na paskach narzędzi. Na paskach narzędzi jest typowe dla polecenia będą wyświetlane tylko ikony (tak, aby zaoszczędzić miejsce na) podczas w menu, że polecenia pojawi się zazwyczaj z zarówno ikonę i tekst.

 Ikony są 16 pikseli szerokości i wysokości 16 pikseli i może być 8-bitowej głębi kolorów (256 kolorów) lub 32-bitowej głębi kolorów (kolor true). ikon koloru 32-bitowe są preferowane. Ikony zwykle są rozmieszczone w jednym wierszu poziomy w postaci bitmapy, chociaż wiele mapy bitowe są dozwolone. Ta mapa bitowa jest zadeklarowana w *vsct* plików wraz z poszczególnych ikon dostępnych w mapie bitowej. Zobacz odwołanie do [Bitmaps, element](../extensibility/bitmaps-element.md) Aby uzyskać więcej informacji.

## <a name="add-an-icon-to-a-command"></a>Dodaj ikonę do polecenia
 W poniższej procedurze przyjęto, że masz istniejący projekt pakietu VSPackage przy użyciu polecenia menu. Aby dowiedzieć się, jak to zrobić, zobacz [Tworzenie rozszerzenia za pomocą polecenia menu](../extensibility/creating-an-extension-with-a-menu-command.md).

1. Tworzenie mapy bitowej o głębi kolorów 32 bity. Ikona jest zawsze 16 x 16, więc tej mapy bitowej muszą być 16 pikseli i wielokrotnością liczby 16 pikseli szerokości.

     Każda ikona jest umieszczany na mapę bitową obok siebie w jednym wierszu. Kanał alfa umożliwia wskazanie miejsc przejrzystości każda ikona.

     Jeśli korzystasz z 8-bitowej głębi kolorów, użyj amarantowy, `RGB(255,0,255)`, jako przejrzystości. Jednak ikon koloru 32-bitowe są preferowane.

2. Skopiuj plik ikony *zasobów* katalogu projektu pakietu VSPackage. W **Eksploratora rozwiązań**, Dodaj ikonę do projektu. (Wybierz **zasobów**i na kliknięcie menu kontekstowe **Dodaj**, następnie **istniejący element**i wybierz swój plik ikony.)

3. Otwórz *vsct* plik w edytorze.

4. Dodaj `GuidSymbol` elementu o nazwie **testIcon**. Utwórz identyfikator GUID (**narzędzia** > **Utwórz GUID**, a następnie wybierz **Format rejestru** i kliknij przycisk **kopiowania**) i wklej go do `value` atrybutu. Wynik powinien wyglądać następująco:

    ```xml
    <!-- Create your own GUID -->
    <GuidSymbol name="testIcon" value="{00000000-0000-0000-0000-0000}">
    ```

5. Dodaj `<IDSymbol>` ikony. `name` Atrybut jest identyfikator ikony i `value` wskazuje swoją pozycję na taśmy, jeśli istnieje. Jeśli istnieje tylko jedna ikona, należy dodać 1. Wynik powinien wyglądać następująco:

    ```xml
    <!-- Create your own GUID -->
    <GuidSymbol name="testIcon" value="{00000000-0000-0000-0000-0000}">
        <IDSymbol name="testIcon1" value="1" />
    </GuidSymbol>
    ```

6. Tworzenie `<Bitmap>` w `<Bitmaps>` części *vsct* pliku do reprezentowania mapy bitowej zawierający ikony.

    - Ustaw `guid` wartość odpowiadającą nazwie `<GuidSymbol>` elementu utworzonego w poprzednim kroku.

    - Ustaw `href` wartość względną ścieżką pliku mapy bitowej (w tym przypadku **zasobów\\< nazwa pliku ikony\>** .

    - Ustaw `usedList` wartość IDSymbol, została utworzona wcześniej. Ten atrybut określa rozdzielana przecinkami lista ikon, które zostaną użyte w pakietu VSPackage. Ikony nie ma na liście są wykluczone formularza kompilacji.

         Blok mapy bitowej powinien wyglądać następująco:

        ```xml
        <Bitmap guid="testIcon" href="Resources\<icon file name>" usedList="testIcon1"/>
        ```

7. W istniejącym `<Button>` elementu, ustaw `Icon` elementu GUIDSymbol i IDSymbol utworzonych wcześniej wartości. Poniżej przedstawiono przykład elementu przycisk z tych wartości:

    ```xml
    <Button guid="guidAddIconCmdSet" id="cmdidMyCommand" priority="0x0100" type="Button">
        <Parent guid="guidAddIconCmdSet" id="MyMenuGroup" />
        <Icon guid="testIcon" id="testIcon1" />
        <Strings>
            <ButtonText>My Command name</ButtonText>
        </Strings>
    </Button>
    ```

8. Przetestuj ikona. Skompiluj projekt, a następnie rozpocząć debugowanie. W doświadczalnym wystąpieniu znaleźć polecenia. Należy widoczna ikona została dodana.

## <a name="see-also"></a>Zobacz także
- [Rozszerzanie menu i poleceń](../extensibility/extending-menus-and-commands.md)
- [Odwołanie do schematu VSCT XML](../extensibility/vsct-xml-schema-reference.md)