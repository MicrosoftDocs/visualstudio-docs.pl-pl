---
title: Dodawanie paska narzędzi do okna narzędzi | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- tool windows, adding toolbars
- toolbars [Visual Studio], adding to tool windows
ms.assetid: 172f64b3-87f8-4292-9c1c-65bffa2b0970
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 646384f43a6196bca802998b709285c247e4c378
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2019
ms.locfileid: "60069044"
---
# <a name="add-a-toolbar-to-a-tool-window"></a>Dodawanie paska narzędzi do okna narzędzi
W tym instruktażu pokazano, jak dodać pasek narzędzi do okna narzędzi.

 Pasek narzędzi jest pasek poziomej lub pionowej, zawierający przyciski, powiązane polecenia. Długość paska narzędzi w oknie narzędzia jest zawsze taki sam jak szerokość lub wysokość okna narzędzi, w zależności od tego, gdzie jest zadokowany pasek narzędzi.

 W przeciwieństwie do pasków narzędzi w IDE pasek narzędzi w oknie narzędzi musi być zadokowane i nie można przenosić ani dostosowane. Jeśli pakietu VSPackage są zapisywane w kodzie umanaged, pasek narzędzi może być zadokowane na żadnych urządzeniach brzegowych.

 Aby uzyskać więcej informacji o tym, jak dodać pasek narzędzi, zobacz [Dodawanie paska narzędzi](../extensibility/adding-a-toolbar.md).

## <a name="prerequisites"></a>Wymagania wstępne
 Począwszy od programu Visual Studio 2015, możesz nie należy instalować programu Visual Studio SDK z Centrum pobierania. Jest dołączony jako opcjonalna funkcja w Instalatorze programu Visual Studio. Możesz także zainstalować zestaw SDK programu VS później. Aby uzyskać więcej informacji, zobacz [instalowania programu Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).

## <a name="create-a-toolbar-for-a-tool-window"></a>Utwórz pasek narzędzi okna narzędzi

1. Utwórz projekt VSIX, o nazwie `TWToolbar` zawierający zarówno polecenie menu o nazwie **TWTestCommand** i okna narzędzi o nazwie **TestToolWindow**. Aby uzyskać więcej informacji, zobacz [Tworzenie rozszerzenia za pomocą polecenia menu](../extensibility/creating-an-extension-with-a-menu-command.md) i [Tworzenie rozszerzenia za pomocą okna narzędzia](../extensibility/creating-an-extension-with-a-tool-window.md). Musisz dodać szablon elementu polecenia przed dodaniem szablonu okna narzędzia.

2. W *TWTestCommandPackage.vsct*, poszukaj sekcji symboli. W węźle GuidSymbol, o nazwie guidTWTestCommandPackageCmdSet zadeklarować paska narzędzi i pasek narzędzi grupy, w następujący sposób.

    ```xml
    <IDSymbol name="TWToolbar" value="0x1000" />
    <IDSymbol name="TWToolbarGroup" value="0x1050" />
    ```

3. W górnej części `Commands` sekcji, Utwórz `Menus` sekcji. Dodaj `Menu` elementu, aby zdefiniować na pasku narzędzi.

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

     Nie można zagnieżdżać pasków narzędzi takich jak podmenu. W związku z tym nie trzeba przypisać element nadrzędny. Ponadto nie trzeba ustawić priorytet, ponieważ użytkownik może przenieść pasków narzędzi. Zazwyczaj początkowe położenie paska narzędzi jest zdefiniowany programowo, ale kolejne zmiany przez użytkownika są zachowywane.

4. W sekcji grupy zdefiniować grupy w celu uwzględnienia poleceń dla paska narzędzi.

    ```xml

    <Group guid="guidTWTestCommandPackageCmdSet" id="TWToolbarGroup" priority="0x0000">
        <Parent guid="guidTWTestCommandPackageCmdSet" id="TWToolbar" />
    </Group>
    ```

5. W sekcji przyciski Zmień nadrzędnego istniejącego elementu przycisk do grupy pasek narzędzi, tak aby zostanie wyświetlony pasek narzędzi.

    ```xml
    <Button guid="guidTWTestCommandPackageCmdSet" id="TWTestCommandId" priority="0x0100" type="Button">
        <Parent guid="guidTWTestCommandPackageCmdSet" id="TWToolbarGroup" />
        <Icon guid="guidImages" id="bmpPic1" />
        <Strings>
            <ButtonText>Invoke TWTestCommand</ButtonText>
        </Strings>
    </Button>
    ```

     Domyślnie jeśli pasek narzędzi ma żadne polecenia nie ma.

     Ponieważ nowy pasek narzędzi nie jest automatycznie dodawany do okna narzędzi, można jawnie dodać pasek narzędzi. Ta czynność została omówiona w następnej sekcji.

## <a name="add-the-toolbar-to-the-tool-window"></a>Dodaj pasek narzędzi do okna narzędzi

1. W *TWTestCommandPackageGuids.cs* Dodaj następujące wiersze.

    ```csharp
    public const string guidTWTestCommandPackageCmdSet = "00000000-0000-0000-0000-0000";  // get the GUID from the .vsct file
    public const int TWToolbar = 0x1000;
    ```

2. W *TestToolWindow.cs* Dodaj następującą instrukcję using.

    ```csharp
    using System.ComponentModel.Design;
    ```

3. W Konstruktorze TestToolWindow Dodaj następujący wiersz.

    ```csharp
    this.ToolBar = new CommandID(new Guid(TWTestCommandPackageGuids.guidTWTestCommandPackageCmdSet), TWTestCommandPackageGuids.TWToolbar);
    ```

## <a name="test-the-toolbar-in-the-tool-window"></a>Test paska narzędzi w oknie narzędzia

1. Skompiluj projekt, a następnie rozpocząć debugowanie. Wystąpienie eksperymentalne programu Visual Studio powinny być wyświetlane.

2. Na **widok / inne Windows** menu, kliknij przycisk **ToolWindow testu** do wyświetlenia okna narzędzia.

     Powinien pojawić się narzędzi (wygląda jak ikona domyślna), u góry po lewej części okna narzędzia tuż poniżej tytułu.

3. Na pasku narzędzi kliknij ikonę, aby wyświetlić komunikat **TWTestCommandPackage wewnątrz TWToolbar.TWTestCommand.MenuItemCallback()**.

## <a name="see-also"></a>Zobacz także
- [Dodawanie paska narzędzi](../extensibility/adding-a-toolbar.md)