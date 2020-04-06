---
title: Dodawanie ikon do poleceń menu | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
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
ms.openlocfilehash: f4b71f981472451766f526cf62e975e571cf46da
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80740151"
---
# <a name="add-icons-to-menu-commands"></a>Dodawanie ikon do poleceń menu
Polecenia mogą pojawiać się zarówno w menu, jak i na paskach narzędzi. Na paskach narzędzi często wyświetlane jest polecenie z tylko ikoną (aby zaoszczędzić miejsce), podczas gdy w menu zwykle pojawia się polecenie z ikoną i tekstem.

 Ikony mają 16 pikseli szerokości i 16 pikseli wysokości i mogą mieć 8-bitową głębię kolorów (256 kolorów) lub 32-bitową głębię kolorów (prawdziwy kolor). Preferowane są 32-bitowe ikony kolorów. Ikony są zazwyczaj rozmieszczone w jednym wierszu poziomym w jednej mapie bitowej, chociaż wiele map bitowych jest dozwolonych. Ta mapa bitowa jest zadeklarowana w pliku *vsct* wraz z poszczególnymi ikonami dostępnymi w mapie bitowej. Zobacz odwołanie do [bitmapy element, aby](../extensibility/bitmaps-element.md) uzyskać więcej informacji.

## <a name="add-an-icon-to-a-command"></a>Dodawanie ikony do polecenia
 Poniższa procedura zakłada, że masz istniejący projekt VSPackage z poleceniem menu. Aby dowiedzieć się, jak to zrobić, zobacz [Tworzenie rozszerzenia za pomocą polecenia menu](../extensibility/creating-an-extension-with-a-menu-command.md).

1. Utwórz mapę bitową z głębią kolorów 32 bitów. Ikona jest zawsze 16 x 16, więc ta mapa bitowa musi mieć wysokość 16 pikseli i wielokrotność 16 pikseli szerokości.

     Każda ikona jest umieszczana na mapie bitowej obok siebie w jednym wierszu. Użyj kanału alfa, aby wskazać miejsca przezroczystości w każdej ikonie.

     Jeśli używasz 8-bitowej głębi kolorów, `RGB(255,0,255)`użyj magenta, jako przezroczystości. Preferowane są jednak 32-bitowe ikony kolorów.

2. Skopiuj plik ikony do katalogu *Zasoby* w projekcie VSPackage. W **Eksploratorze rozwiązań**dodaj ikonę do projektu. (Wybierz **zasoby**, a w menu kontekstowym kliknij polecenie **Dodaj**, a następnie **pozycję Istniejący element**i wybierz plik ikony).

3. Otwórz plik *vsct* w edytorze.

4. Dodaj `GuidSymbol` element o nazwie **testIcon**. Utwórz identyfikator GUID **(Narzędzia** > **Tworzenie identyfikatora GUID,** a następnie `value` wybierz pozycję Format **rejestru** i kliknij pozycję **Kopiuj)** i wklej go do atrybutu. Wynik powinien wyglądać następująco:

    ```xml
    <!-- Create your own GUID -->
    <GuidSymbol name="testIcon" value="{00000000-0000-0000-0000-0000}">
    ```

5. Dodaj `<IDSymbol>` ikonę. Atrybut `name` jest identyfikatorem ikony, a `value` jego położenie na pasku, jeśli istnieje. Jeśli jest tylko jedna ikona, dodaj 1. Wynik powinien wyglądać następująco:

    ```xml
    <!-- Create your own GUID -->
    <GuidSymbol name="testIcon" value="{00000000-0000-0000-0000-0000}">
        <IDSymbol name="testIcon1" value="1" />
    </GuidSymbol>
    ```

6. Utwórz `<Bitmap>` w `<Bitmaps>` sekcji pliku *vsct* do reprezentowania mapy bitowej zawierającej ikony.

    - Ustaw `guid` wartość na nazwę `<GuidSymbol>` elementu utworzonego w poprzednim kroku.

    - Ustaw `href` wartość względnej ścieżki pliku mapy bitowej (w tym przypadku **nazwy pliku\\ \>ikony Zasoby<**.

    - Ustaw `usedList` wartość na IDSymbol utworzony wcześniej. Ten atrybut określa listę rozdzielanych przecinkami ikon, które mają być używane w vspackage. Ikony niena liście są wykluczone kompilacji formularza.

         Blok mapy bitowej powinien wyglądać następująco:

        ```xml
        <Bitmap guid="testIcon" href="Resources\<icon file name>" usedList="testIcon1"/>
        ```

7. W istniejącym `<Button>` elemencie ustaw `Icon` element na wartości GUIDSymbol i IDSymbol utworzone wcześniej. Oto przykład Button element z tych wartości:

    ```xml
    <Button guid="guidAddIconCmdSet" id="cmdidMyCommand" priority="0x0100" type="Button">
        <Parent guid="guidAddIconCmdSet" id="MyMenuGroup" />
        <Icon guid="testIcon" id="testIcon1" />
        <Strings>
            <ButtonText>My Command name</ButtonText>
        </Strings>
    </Button>
    ```

8. Przetestuj swoją ikonę. Skompiluj projekt i rozpocznij debugowanie. W wystąpieniu eksperymentalnym znajdź polecenie. Powinna ona wyświetlać dodaną ikonę.

## <a name="see-also"></a>Zobacz też
- [Rozszerzanie menu i poleceń](../extensibility/extending-menus-and-commands.md)
- [Odwołanie do schematu XML VSCT](../extensibility/vsct-xml-schema-reference.md)
