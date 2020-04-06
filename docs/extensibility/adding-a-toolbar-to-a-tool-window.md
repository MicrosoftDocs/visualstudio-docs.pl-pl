---
title: Dodawanie paska narzędzi do okna narzędzia | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- tool windows, adding toolbars
- toolbars [Visual Studio], adding to tool windows
ms.assetid: 172f64b3-87f8-4292-9c1c-65bffa2b0970
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 094515eb94279623974bd7b55cc9923c49625a70
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80740243"
---
# <a name="add-a-toolbar-to-a-tool-window"></a>Dodawanie paska narzędzi do okna narzędzia
W tym przewodniku pokazano, jak dodać pasek narzędzi do okna narzędzia.

 Pasek narzędzi to poziomy lub pionowy pasek zawierający przyciski powiązane z poleceniami. Długość paska narzędzi w oknie narzędzia jest zawsze taka sama jak szerokość lub wysokość okna narzędzia, w zależności od miejsca zadokowania paska narzędzi.

 W przeciwieństwie do pasków narzędzi w IDE, pasek narzędzi w oknie narzędzia musi być zadokowany i nie można go przenieść ani dostosować. Jeśli VSPackage jest napisany w umanaged kodu, pasek narzędzi może być zadokowany na dowolnej krawędzi.

 Aby uzyskać więcej informacji na temat dodawania paska narzędzi, zobacz [Dodawanie paska narzędzi](../extensibility/adding-a-toolbar.md).

## <a name="prerequisites"></a>Wymagania wstępne
 Począwszy od programu Visual Studio 2015, nie należy instalować visual studio SDK z centrum pobierania. Jest on dołączony jako opcjonalna funkcja w konfiguracji programu Visual Studio. Można również zainstalować vs SDK później. Aby uzyskać więcej informacji, zobacz [Instalowanie zestawu SDK programu Visual Studio](../extensibility/installing-the-visual-studio-sdk.md).

## <a name="create-a-toolbar-for-a-tool-window"></a>Tworzenie paska narzędzi dla okna narzędzia

1. Utwórz projekt VSIX o nazwie, `TWToolbar` który ma zarówno polecenie menu o nazwie **TWTestCommand,** jak i okno narzędzia o nazwie **TestToolWindow**. Aby uzyskać więcej informacji, zobacz [Tworzenie rozszerzenia za pomocą polecenia menu](../extensibility/creating-an-extension-with-a-menu-command.md) i Tworzenie rozszerzenia z [oknem narzędzia](../extensibility/creating-an-extension-with-a-tool-window.md). Przed dodaniem szablonu okna narzędzia należy dodać szablon elementu polecenia.

2. W *TWTestCommandPackage.vsct*poszukaj sekcji Symbole. W węźle GuidSymbol o nazwie guidTWTestCommandPackageCmdSet zadeklarować pasek narzędzi i grupę paska narzędzi, w następujący sposób.

    ```xml
    <IDSymbol name="TWToolbar" value="0x1000" />
    <IDSymbol name="TWToolbarGroup" value="0x1050" />
    ```

3. W górnej części `Commands` sekcji utwórz sekcję. `Menus` Dodaj `Menu` element, aby zdefiniować pasek narzędzi.

    ```xml
    <Menus>
        <Menu guid="guidTWTestCommandPackageCmdSet" id="TWToolbar" type="ToolWindowToolbar">
            <CommandFlag>DefaultDocked</CommandFlag>
            <Strings>
                <ButtonText>Test Toolbar</ButtonText>
                <CommandName>Test Toolbar</CommandName>
            </Strings>
        </Menu>
    </Menus>
    ```

     Paski narzędzi nie mogą być zagnieżdżone jak podmenu. W związku z tym nie trzeba przypisywać nadrzędnego. Ponadto nie trzeba ustawiać priorytetu, ponieważ użytkownik może przenosić paski narzędzi. Zazwyczaj początkowe rozmieszczenie paska narzędzi jest definiowane programowo, ale kolejne zmiany przez użytkownika są utrwalone.

4. W sekcji Grupy zdefiniuj grupę zawierającą polecenia paska narzędzi.

    ```xml

    <Group guid="guidTWTestCommandPackageCmdSet" id="TWToolbarGroup" priority="0x0000">
        <Parent guid="guidTWTestCommandPackageCmdSet" id="TWToolbar" />
    </Group>
    ```

5. W sekcji Przyciski zmień element nadrzędny istniejącego buttona na grupę paska narzędzi, tak aby pasek narzędzi był wyświetlany.

    ```xml
    <Button guid="guidTWTestCommandPackageCmdSet" id="TWTestCommandId" priority="0x0100" type="Button">
        <Parent guid="guidTWTestCommandPackageCmdSet" id="TWToolbarGroup" />
        <Icon guid="guidImages" id="bmpPic1" />
        <Strings>
            <ButtonText>Invoke TWTestCommand</ButtonText>
        </Strings>
    </Button>
    ```

     Domyślnie, jeśli pasek narzędzi nie ma żadnych poleceń, nie jest wyświetlany.

     Ponieważ nowy pasek narzędzi nie jest automatycznie dodawany do okna narzędzia, pasek narzędzi musi zostać dodany jawnie. Ta czynność została omówiona w następnej sekcji.

## <a name="add-the-toolbar-to-the-tool-window"></a>Dodawanie paska narzędzi do okna narzędzia

1. W *TWTestCommandPackageGuids.cs* dodać następujące wiersze.

    ```csharp
    public const string guidTWTestCommandPackageCmdSet = "00000000-0000-0000-0000-0000";  // get the GUID from the .vsct file
    public const int TWToolbar = 0x1000;
    ```

2. W *TestToolWindow.cs* dodać następujące instrukcje.

    ```csharp
    using System.ComponentModel.Design;
    ```

3. W Konstruktorze TestToolWindow dodaj następujący wiersz.

    ```csharp
    this.ToolBar = new CommandID(new Guid(TWTestCommandPackageGuids.guidTWTestCommandPackageCmdSet), TWTestCommandPackageGuids.TWToolbar);
    ```

## <a name="test-the-toolbar-in-the-tool-window"></a>Testowanie paska narzędzi w oknie narzędzia

1. Skompiluj projekt i rozpocznij debugowanie. Powinno pojawić się wystąpienie eksperymentalne programu Visual Studio.

2. W menu **Widok / Inne okna** kliknij polecenie Test **ToolWindow,** aby wyświetlić okno narzędzia.

     W lewym górnym rogu okna narzędzia, tuż pod tytułem, powinien zostać wyświetlony pasek narzędzi (wygląda jak ikona domyślna).

3. Na pasku narzędzi kliknij ikonę, aby wyświetlić komunikat **TWTestCommandPackage Inside TWToolbar.TWTestCommand.MenuItemCallback()**.

## <a name="see-also"></a>Zobacz też
- [Dodawanie paska narzędzi](../extensibility/adding-a-toolbar.md)
