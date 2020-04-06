---
title: Dodawanie podmenu do menu | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- context menus
- submenus, cascading
- cascading submenus
- menus, creating cascading submenus
ms.assetid: 692600cb-d052-40e2-bdae-4354ae7c6c84
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 59c9364d03aab135f7c9b4bf91df21b949e78ee4
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80740269"
---
# <a name="add-a-submenu-to-a-menu"></a>Dodawanie podmenu do menu
Ten instruktaż opiera się na demonstracji w [Dodaj menu do paska menu programu Visual Studio,](../extensibility/adding-a-menu-to-the-visual-studio-menu-bar.md) pokazując, jak dodać podmenu do menu **TestMenu.**

 Podmenu jest menu pomocnicze, które pojawia się w innym menu. Podmenu można zidentyfikować za pomocą strzałki, która następuje po jego nazwie. Kliknięcie nazwy powoduje wyświetlenie podmenu i jego poleceń.

 W tym instruktażu utworzy się podmenu w menu na pasku menu programu Visual Studio i umieszcza nowe polecenie w podmenu. Instruktaż implementuje również nowe polecenie.

## <a name="prerequisites"></a>Wymagania wstępne
 Począwszy od programu Visual Studio 2015, nie należy instalować visual studio SDK z centrum pobierania. Jest on dołączony jako opcjonalna funkcja w konfiguracji programu Visual Studio. Można również zainstalować vs SDK później. Aby uzyskać więcej informacji, zobacz [Instalowanie pakietu SDK programu Visual Studio](../extensibility/installing-the-visual-studio-sdk.md).

## <a name="add-a-submenu-to-a-menu"></a>Dodawanie podmenu do menu

1. Wykonaj kroki opisane w [Dodaj menu do paska menu programu Visual Studio,](../extensibility/adding-a-menu-to-the-visual-studio-menu-bar.md) aby utworzyć element projektu i menu. Kroki opisane w tym instruktażu zakładają, `TopLevelMenu`że nazwa projektu VSIX jest .

2. Otwórz *testCommandPackage.vsct*. W `<Symbols>` sekcji dodaj `<IDSymbol>` element podmenu, jeden dla grupy podmenu i jeden dla polecenia, wszystko w `<GuidSymbol>` węźle o nazwie "guidTopLevelMenuCmdSet". Jest to ten sam `<IDSymbol>` węzeł, który zawiera element menu najwyższego poziomu.

    ```xml
    <IDSymbol name="SubMenu" value="0x1100"/>
    <IDSymbol name="SubMenuGroup" value="0x1150"/>
    <IDSymbol name="cmdidTestSubCommand" value="0x0105"/>
    ```

3. Dodaj nowo utworzone podmenu `<Menus>` do sekcji.

    ```xml
    <Menu guid="guidTestCommandPackageCmdSet" id="SubMenu" priority="0x0100" type="Menu">
        <Parent guid="guidTestCommandPackageCmdSet" id="MyMenuGroup"/>
        <Strings>
            <ButtonText>Sub Menu</ButtonText>
            <CommandName>Sub Menu</CommandName>
        </Strings>
    </Menu>
    ```

     Para identyfikatorów GUID/ID obiektu nadrzędnego określa grupę menu, która została wygenerowana w [menu Dodaj menu do paska menu programu Visual Studio](../extensibility/adding-a-menu-to-the-visual-studio-menu-bar.md)i jest elementem podrzędnym menu najwyższego poziomu.

4. Dodaj grupę menu zdefiniowaną w `<Groups>` kroku 2 do sekcji i uczynić ją elementem podrzędnym podmenu.

    ```xml
    <Group guid="guidTestCommandPackageCmdSet" id="SubMenuGroup" priority="0x0000">
        <Parent guid="guidTestCommandPackageCmdSet" id="SubMenu"/>
    </Group>
    ```

5. Dodaj nowy `<Button>` element `<Buttons>` do sekcji, aby zdefiniować polecenie utworzone w kroku 2 jako element w podmenu.

    ```xml
    <Button guid="guidTestCommandPackageCmdSet" id="cmdidTestSubCommand" priority="0x0000" type="Button">
        <Parent guid="guidTestCommandPackageCmdSet" id="SubMenuGroup" />
        <Icon guid="guidImages" id="bmpPic2" />
        <Strings>
           <CommandName>cmdidTestSubCommand</CommandName>
           <ButtonText>Test Sub Command</ButtonText>
        </Strings>
    </Button>
    ```

6. Skompiluj rozwiązanie i rozpocznij debugowanie. Powinno zostać wyświetlene eksperymentalne wystąpienie.

7. Kliknij **przycisk TestMenu,** aby wyświetlić nowe podmenu o nazwie **Podmenu**. Kliknij **podmenu,** aby otworzyć podmenu i wyświetlić nowe polecenie **Test Podkomendenie**. Należy zauważyć, że kliknięcie **polecenia Test Sub** command nic nie robi.

## <a name="add-a-command"></a>Dodawanie polecenia

1. Otwórz *TestCommand.cs* i dodaj następujący identyfikator polecenia po istniejącym identyfikatorze polecenia.

    ```csharp
    public const int cmdidTestSubCmd = 0x0105;
    ```

2. Dodaj polecenie podrzędne. Znajdź konstruktora poleceń. Dodaj następujące wiersze tuż po `AddCommand` wywołaniu metody.

    ```csharp
    CommandID subCommandID = new CommandID(CommandSet, cmdidTestSubCmd);
    MenuCommand subItem = new MenuCommand(new EventHandler(SubItemCallback), subCommandID);
    commandService.AddCommand(subItem);
    ```

    Program `SubItemCallback` obsługi poleceń zostanie zdefiniowany później. Konstruktor powinien teraz wyglądać następująco:

    ```csharp
    private TestCommand(Package package)
    {
        if (package == null)
        {
            throw new ArgumentNullException("package");
        }

        this.package = package;

        OleMenuCommandService commandService = this.ServiceProvider.GetService(typeof(IMenuCommandService)) as OleMenuCommandService;
        if (commandService != null)
        {
            var menuCommandID = new CommandID(CommandSet, CommandId);
            var menuItem = new MenuCommand(this.MenuItemCallback, menuCommandID);
            commandService.AddCommand(menuItem);

            CommandID subCommandID = new CommandID(CommandSet, cmdidTestSubCmd);
            MenuCommand subItem = new MenuCommand(new EventHandler(SubItemCallback), subCommandID);
            commandService.AddCommand(subItem);
        }
    }
    ```

3. Dodaj `SubItemCallback()`. Jest to metoda, która jest wywoływana po kliknięciu nowego polecenia w podmenu.

    ```csharp
    private void SubItemCallback(object sender, EventArgs e)
    {
        IVsUIShell uiShell = (IVsUIShell)this.ServiceProvider.GetServiceAsync(typeof(SVsUIShell));
        Guid clsid = Guid.Empty;
        int result;
        uiShell.ShowMessageBox(
            0,
            ref clsid,
            "TestCommand",
            string.Format(CultureInfo.CurrentCulture,
            "Inside TestCommand.SubItemCallback()",
            this.ToString()),
            string.Empty,
            0,
            OLEMSGBUTTON.OLEMSGBUTTON_OK,
            OLEMSGDEFBUTTON.OLEMSGDEFBUTTON_FIRST,
            OLEMSGICON.OLEMSGICON_INFO,
            0,
            out result);
    }
    ```

4. Skompiluj projekt i rozpocznij debugowanie. Powinno pojawić się wystąpienie eksperymentalne.

5. W menu **TestMenu** kliknij polecenie **Podmenu,** a następnie kliknij polecenie **Testuj polecenie podrzędne**. Powinno pojawić się okno komunikatu i wyświetlić tekst "Test Command Inside TestCommand.SubItemCallback()".

## <a name="see-also"></a>Zobacz też

- [Dodawanie menu do paska menu programu Visual Studio](../extensibility/adding-a-menu-to-the-visual-studio-menu-bar.md)
- [Polecenia, menu i paski narzędzi](../extensibility/internals/commands-menus-and-toolbars.md)
