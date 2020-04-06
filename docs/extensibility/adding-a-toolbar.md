---
title: Dodawanie paska narzędzi | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- toolbars [Visual Studio], adding to IDE
- IDE, adding toolbars
ms.assetid: 17302c25-6f59-4e97-8c85-54f95336a07f
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 655cd87fe59cf4f42361cc24a63eb56653caae1a
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80740216"
---
# <a name="add-a-toolbar"></a>Dodawanie paska narzędzi
W tym przewodniku pokazano, jak dodać pasek narzędzi do środowiska IDE programu Visual Studio.

 Pasek narzędzi to poziomy lub pionowy pasek zawierający przyciski powiązane z poleceniami. W zależności od jego implementacji pasek narzędzi w IDE można zmienić położenie, zadokowany po dowolnej stronie głównego okna IDE lub wykonane, aby pozostać przed innymi oknami.

 Ponadto użytkownicy mogą dodawać polecenia do paska narzędzi lub usuwać je z niego za pomocą okna dialogowego **Dostosowywanie.** Zazwyczaj paski narzędzi w vspackages są konfigurowalne przez użytkownika. IDE obsługuje wszystkie dostosowania i VSPackage odpowiada na polecenia. VSPackage nie musi wiedzieć, gdzie fizycznie znajduje się polecenie.

 Aby uzyskać więcej informacji o menu, zobacz [Polecenia, menu i paski narzędzi](../extensibility/internals/commands-menus-and-toolbars.md).

## <a name="prerequisites"></a>Wymagania wstępne
 Począwszy od programu Visual Studio 2015, nie należy instalować visual studio SDK z centrum pobierania. Jest on dołączony jako opcjonalna funkcja w konfiguracji programu Visual Studio. Można również zainstalować vs SDK później. Aby uzyskać więcej informacji, zobacz [Instalowanie pakietu SDK programu Visual Studio](../extensibility/installing-the-visual-studio-sdk.md).

## <a name="create-an-extension-with-a-toolbar"></a>Tworzenie rozszerzenia za pomocą paska narzędzi
 Utwórz projekt VSIX o nazwie `IDEToolbar`. Dodaj szablon elementu polecenia menu o nazwie **ToolbarTestCommand**. Aby uzyskać informacje na temat tego, jak to zrobić, zobacz [Tworzenie rozszerzenia za pomocą polecenia menu](../extensibility/creating-an-extension-with-a-menu-command.md).

## <a name="create-a-toolbar-for-the-ide"></a>Tworzenie paska narzędzi dla IDE

1. W *polu ToolbarTestCommandPackage.vsct*poszukaj sekcji Symbole. W GuidSymbol element o nazwie guidToolbarTestCommandPackageCmdSet, dodaj deklaracje dla paska narzędzi i grupy paska narzędzi, w następujący sposób.

    ```xml
    <IDSymbol name="Toolbar" value="0x1000" />
    <IDSymbol name="ToolbarGroup" value="0x1050" />

    ```

2. U góry sekcji Polecenia utwórz sekcję Menu. Dodaj element Menu do sekcji Menu, aby zdefiniować pasek narzędzi.

    ```xml
    <Menus>
        <Menu guid="guidToolbarTestCommandPackageCmdSet" id="Toolbar"
            type="Toolbar" >
            <CommandFlag>DefaultDocked</CommandFlag>
            <Strings>
                <ButtonText>Test Toolbar</ButtonText>
                <CommandName>Test Toolbar</CommandName>
            </Strings>
          </Menu>
    </Menus>
    ```

     Paski narzędzi nie mogą być zagnieżdżone jak podmenu. W związku z tym nie trzeba przypisywać grupy nadrzędnej. Ponadto nie trzeba ustawiać priorytetu, ponieważ użytkownik może przenosić paski narzędzi. Zazwyczaj początkowe rozmieszczenie paska narzędzi jest definiowane programowo, ale kolejne zmiany przez użytkownika są utrwalone.

3. W sekcji [Grupy](../extensibility/groups-element.md) po wprowadzeniu istniejącej grupy zdefiniuj element [Grupy,](../extensibility/group-element.md) który zawiera polecenia paska narzędzi.

    ```xml
    <Group guid="guidToolbarTestCommandPackageCmdSet" id="ToolbarGroup"
          priority="0x0000">
      <Parent guid="guidToolbarTestCommandPackageCmdSet" id="Toolbar"/>
    </Group>
    ```

4. Wyświetl przycisk na pasku narzędzi. W sekcji Przyciski zastąp blok nadrzędny na pasku narzędzi Button. Wynikowy button bloku powinien wyglądać następująco:

    ```xml
    <Button guid="guidToolbarTestCommandPackageCmdSet" id="ToolbarTestCommandId" priority="0x0100" type="Button">
        <Parent guid= "guidToolbarTestCommandPackageCmdSet" id="ToolbarGroup" />
                <Icon guid="guidImages" id="bmpPic1" />
        <Strings>
            <ButtonText>Invoke ToolbarTestCommand</ButtonText>
        </Strings>
    </Button>
    ```

     Domyślnie, jeśli pasek narzędzi nie ma żadnych poleceń, nie jest wyświetlany.

5. Skompiluj projekt i rozpocznij debugowanie. Powinno pojawić się wystąpienie eksperymentalne.

6. Kliknij prawym przyciskiem myszy pasek menu programu Visual Studio, aby uzyskać listę pasków narzędzi. Wybierz **pozycję Test Toolbar**.

7. Pasek narzędzi powinien być teraz widoczny jako ikona po prawej stronie ikony Znajdź w plikach. Po kliknięciu ikony powinien zostać wyświetlony komunikat z napisem **ToolbarTestCommandPackage. Wewnątrz IDEToolbar.ToolbarTestCommand.MenuItemCallback()**.

## <a name="see-also"></a>Zobacz też
- [Polecenia, menu i paski narzędzi](../extensibility/internals/commands-menus-and-toolbars.md)
