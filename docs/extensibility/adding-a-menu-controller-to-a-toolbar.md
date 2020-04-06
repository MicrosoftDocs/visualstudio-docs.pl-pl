---
title: Dodawanie kontrolera menu do paska narzędzi | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- toolbars [Visual Studio], adding menu controllers
- menus, adding menu controllers to toolbars
- menu controllers, adding to toolbars
ms.assetid: 6af9b0b4-037f-404c-bb40-aaa1970768ea
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: d4dcb9e51f6633476a8f0eadea30da513e5ef760
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80740321"
---
# <a name="add-a-menu-controller-to-a-toolbar"></a>Dodawanie kontrolera menu do paska narzędzi
Ten instruktaż jest na podstawie [przewodnika Dodaj pasek narzędzi do okna narzędzia](../extensibility/adding-a-toolbar-to-a-tool-window.md) i pokazuje, jak dodać kontroler menu do paska narzędzi. Kroki pokazane tutaj również mogą być stosowane do paska narzędzi, który jest tworzony w [Add a toolbar](../extensibility/adding-a-toolbar.md) instrurough.

Kontroler menu jest formantem podzielonym. Po lewej stronie kontrolera menu jest wyświetlane ostatnie używane polecenie i można je uruchomić, klikając je. Po prawej stronie kontrolera menu znajduje się strzałka, która po kliknięciu otwiera listę dodatkowych poleceń. Po kliknięciu polecenia na liście polecenie jest uruchamiane i zastępuje polecenie po lewej stronie kontrolera menu. W ten sposób kontroler menu działa jak przycisk polecenia, który zawsze pokazuje ostatnio używane polecenie z listy.

Kontrolery menu mogą pojawiać się w menu, ale są najczęściej używane na paskach narzędzi.

## <a name="prerequisites"></a>Wymagania wstępne
Począwszy od programu Visual Studio 2015, nie należy instalować visual studio SDK z centrum pobierania. Jest on dołączony jako opcjonalna funkcja w konfiguracji programu Visual Studio. Można również zainstalować vs SDK później. Aby uzyskać więcej informacji, zobacz [Instalowanie pakietu SDK programu Visual Studio](../extensibility/installing-the-visual-studio-sdk.md).

## <a name="create-a-menu-controller"></a>Tworzenie kontrolera menu

1. Postępuj zgodnie z procedurami opisanymi w [oknie narzędzia Dodawanie paska narzędzi,](../extensibility/adding-a-toolbar-to-a-tool-window.md) aby utworzyć okno narzędzia z paskiem narzędzi.

2. W *TWTestCommandPackage.vsct*przejdź do sekcji Symbole. W GuidSymbol element o nazwie **guidTWTestCommandPackageCmdSet**, zadeklarować kontroler menu, grupa kontrolera menu i trzy elementy menu.

    ```xml
    <IDSymbol name="TestMenuController" value="0x1300" /><IDSymbol name="TestMenuControllerGroup" value="0x1060" /><IDSymbol name="cmdidMCItem1" value="0x0130" /><IDSymbol name="cmdidMCItem2" value="0x0131" /><IDSymbol name="cmdidMCItem3" value="0x0132" />
    ```

3. W sekcji Menu po ostatnim wpisie menu zdefiniuj kontroler menu jako menu.

    ```xml
    <Menu guid="guidTWTestCommandPackageCmdSet" id="TestMenuController" priority="0x0100" type="MenuController">
        <Parent guid="guidTWTestCommandPackageCmdSet" id="TWToolbarGroup" />
        <CommandFlag>IconAndText</CommandFlag>
        <CommandFlag>TextChanges</CommandFlag>
        <CommandFlag>TextIsAnchorCommand</CommandFlag>
        <Strings>
            <ButtonText>Test Menu Controller</ButtonText>
            <CommandName>Test Menu Controller</CommandName>
        </Strings>
    </Menu>
    ```

    Flagi `TextChanges` `TextIsAnchorCommand` i muszą być dołączone, aby kontroler menu odzwierciedlał ostatnio wybrane polecenie.

4. W sekcji Grupy po ostatnim wpisie grupy dodaj grupę kontrolera menu.

    ```xml
    <Group guid="guidTWTestCommandPackageCmdSet" id="TestMenuControllerGroup" priority="0x000">
        <Parent guid="guidTWTestCommandPackageCmdSet" id="TestMenuController" />
    </Group>
    ```

    Ustawiając kontroler menu jako element nadrzędny, wszystkie polecenia umieszczone w tej grupie są wyświetlane w kontrolerze menu. Atrybut `priority` jest pomijany, co ustawia go na wartość domyślną 0, ponieważ jest to jedyna grupa na kontrolerze menu.

5. W sekcji Przyciski po ostatnim wprowadzeniu przycisku dodaj buttona dla każdego elementu menu.

    ```xml
    <Button guid="guidTWTestCommandPackageCmdSet" id="cmdidMCItem1" priority="0x0000" type="Button">
        <Parent guid="guidTWTestCommandPackageCmdSet" id="TestMenuControllerGroup" />
        <Icon guid="guidImages" id="bmpPic1" />
        <CommandFlag>IconAndText</CommandFlag>
        <Strings>
            <ButtonText>MC Item 1</ButtonText>
            <CommandName>MC Item 1</CommandName>
        </Strings>
    </Button>
    <Button guid="guidTWTestCommandPackageCmdSet" id="cmdidMCItem2" priority="0x0100" type="Button">
        <Parent guid="guidTWTestCommandPackageCmdSet" id="TestMenuControllerGroup" />
        <Icon guid="guidImages" id="bmpPic2" />
        <CommandFlag>IconAndText</CommandFlag>
        <Strings>
            <ButtonText>MC Item 2</ButtonText>
            <CommandName>MC Item 2</CommandName>
        </Strings>
    </Button>
    <Button guid="guidTWTestCommandPackageCmdSet" id="cmdidMCItem3" priority="0x0200" type="Button">
        <Parent guid="guidTWTestCommandPackageCmdSet" id="TestMenuControllerGroup" />
        <Icon guid="guidImages" id="bmpPicSearch" />
        <CommandFlag>IconAndText</CommandFlag>
        <Strings>
            <ButtonText>MC Item 3</ButtonText>
            <CommandName>MC Item 3</CommandName>
        </Strings>
    </Button>
    ```

6. W tym momencie można spojrzeć na kontroler menu. Skompiluj projekt i rozpocznij debugowanie. Powinno zostać wyświetlene eksperymentalne wystąpienie.

   1. W menu **Widok / Inne okna** otwórz okno Test **ToolWindow**.

   2. Kontroler menu pojawi się na pasku narzędzi w oknie narzędzia.

   3. Kliknij strzałkę po prawej stronie kontrolera menu, aby wyświetlić trzy możliwe polecenia.

      Należy zauważyć, że po kliknięciu polecenia, tytuł kontrolera menu zmienia się, aby wyświetlić to polecenie. W następnej sekcji dodamy kod, aby aktywować te polecenia.

## <a name="implement-the-menu-controller-commands"></a>Implementowanie poleceń kontrolera menu

1. W *TWTestCommandPackageGuids.cs*, dodaj identyfikatory poleceń dla trzech elementów menu po istniejących identyfikatorach poleceń.

    ```csharp
    public const int cmdidMCItem1 = 0x130;
    public const int cmdidMCItem2 = 0x131;
    public const int cmdidMCItem3 = 0x132;
    ```

2. W *TWTestCommand.cs*, dodaj następujący kod w górnej `TWTestCommand` części klasy.

    ```csharp
    private int currentMCCommand; // The currently selected menu controller command
    ```

3. W konstruktorze TWTestCommand, po `AddCommand` ostatnim wywołaniu metody, dodaj kod do kierowania zdarzeń dla każdego polecenia za pośrednictwem tych samych programów obsługi.

    ```csharp
    for (int i = TWTestCommandPackageGuids.cmdidMCItem1; i <=
        TWTestCommandPackageGuids.cmdidMCItem3; i++)
    {
        CommandID cmdID = new
        CommandID(new Guid(TWTestCommandPackageGuids.guidTWTestCommandPackageCmdSet), i);
        OleMenuCommand mc = new OleMenuCommand(new
          EventHandler(OnMCItemClicked), cmdID);
        mc.BeforeQueryStatus += new EventHandler(OnMCItemQueryStatus);
        commandService.AddCommand(mc);
        // The first item is, by default, checked. 
        if (TWTestCommandPackageGuids.cmdidMCItem1 == i)
        {
            mc.Checked = true;
            this.currentMCCommand = i;
        }
    }
    ```

4. Dodaj program obsługi zdarzeń do klasy **TWTestCommand,** aby oznaczyć wybrane polecenie jako zaznaczone.

    ```csharp
    private void OnMCItemQueryStatus(object sender, EventArgs e)
    {
        OleMenuCommand mc = sender as OleMenuCommand;
        if (null != mc)
        {
            mc.Checked = (mc.CommandID.ID == this.currentMCCommand);
        }
    }
    ```

5. Dodaj program obsługi zdarzeń, który wyświetla MessageBox, gdy użytkownik wybierze polecenie na kontrolerze menu:

    ```csharp
    private void OnMCItemClicked(object sender, EventArgs e)
    {
        OleMenuCommand mc = sender as OleMenuCommand;
        if (null != mc)
        {
            string selection;
            switch (mc.CommandID.ID)
            {
                case c.cmdidMCItem1:
                    selection = "Menu controller Item 1";
                    break;

                case TWTestCommandPackageGuids.cmdidMCItem2:
                    selection = "Menu controller Item 2";
                    break;

                case TWTestCommandPackageGuids.cmdidMCItem3:
                    selection = "Menu controller Item 3";
                    break;

                default:
                    selection = "Unknown command";
                    break;
            }
            this.currentMCCommand = mc.CommandID.ID;

            IVsUIShell uiShell =
              (IVsUIShell) ServiceProvider.GetService(typeof(SVsUIShell));
            Guid clsid = Guid.Empty;
            int result;
            uiShell.ShowMessageBox(
                    0,
                    ref clsid,
                    "Test Tool Window Toolbar Package",
                    string.Format(CultureInfo.CurrentCulture,
                                 "You selected {0}", selection),
                    string.Empty,
                    0,
                    OLEMSGBUTTON.OLEMSGBUTTON_OK,
                    OLEMSGDEFBUTTON.OLEMSGDEFBUTTON_FIRST,
                    OLEMSGICON.OLEMSGICON_INFO,
                    0,
                    out result);
        }
    }
    ```

## <a name="testing-the-menu-controller"></a>Testowanie kontrolera menu

1. Skompiluj projekt i rozpocznij debugowanie. Powinno zostać wyświetlene eksperymentalne wystąpienie.

2. Otwórz **okno testowe NarzędziaWindow** w menu **Widok / Inne okna.**

    Kontroler menu pojawi się na pasku narzędzi w oknie narzędzia i wyświetli **pozycję MC Item 1**.

3. Kliknij przycisk kontrolera menu po lewej stronie strzałki.

    Powinieneś zobaczyć trzy elementy, z których pierwszy jest zaznaczony i ma pole podświetlenia wokół jego ikony. Kliknij **pozycję Mc Item 3**.

    Zostanie wyświetlone okno dialogowe z **komunikatem Wybrano pozycję 3 kontrolera menu**. Należy zauważyć, że komunikat odpowiada tekstowi na przycisku kontrolera menu. Przycisk kontrolera menu wyświetla teraz **pozycję MC Item 3**.

## <a name="see-also"></a>Zobacz też
- [Dodawanie paska narzędzi do okna narzędzia](../extensibility/adding-a-toolbar-to-a-tool-window.md)
- [Dodawanie paska narzędzi](../extensibility/adding-a-toolbar.md)
