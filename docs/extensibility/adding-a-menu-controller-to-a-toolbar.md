---
title: Dodawanie kontrolera menu do paska narzędzi | Microsoft Docs
description: Dowiedz się, jak utworzyć kontroler menu i dodać go do paska narzędzi okna narzędzia w programie Visual Studio, a następnie zaimplementować polecenia kontrolera menu i je przetestować.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- toolbars [Visual Studio], adding menu controllers
- menus, adding menu controllers to toolbars
- menu controllers, adding to toolbars
ms.assetid: 6af9b0b4-037f-404c-bb40-aaa1970768ea
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 304f4ea11abc332c01603f96b6b67c0bd22e38c6
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/25/2021
ms.locfileid: "105060071"
---
# <a name="add-a-menu-controller-to-a-toolbar"></a>Dodawanie kontrolera menu do paska narzędzi
Ten przewodnik kompiluje się na stronie [Dodawanie paska narzędzi do](../extensibility/adding-a-toolbar-to-a-tool-window.md) przewodnika po oknie narzędzia i pokazuje, jak dodać kontroler menu do paska narzędzi okna narzędzi. Kroki przedstawione w tym miejscu można również zastosować do paska narzędzi, który został utworzony w przewodniku [Dodawanie paska narzędzi](../extensibility/adding-a-toolbar.md) .

Kontroler menu jest formantem podzielonym. Lewa strona kontrolera menu pokazuje ostatnio używane polecenie i można uruchomić ją, klikając ją. Prawa strona kontrolera menu jest strzałką, która po kliknięciu otwiera listę dodatkowych poleceń. Po kliknięciu polecenia na liście zostanie uruchomione polecenie, które zastępuje polecenie po lewej stronie kontrolera menu. W ten sposób kontroler menu działa jak przycisk polecenia, który zawsze pokazuje ostatnio używane polecenie z listy.

Kontrolery menu mogą znajdować się w menu, ale najczęściej są używane na paskach narzędzi.

## <a name="prerequisites"></a>Wymagania wstępne
Począwszy od programu Visual Studio 2015, nie należy instalować zestawu Visual Studio SDK z centrum pobierania. Jest ona dostępna jako opcjonalna funkcja w Instalatorze programu Visual Studio. Zestaw VS SDK można także zainstalować później. Aby uzyskać więcej informacji, zobacz [Instalowanie zestawu Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).

## <a name="create-a-menu-controller"></a>Tworzenie kontrolera menu

1. Postępuj zgodnie z procedurami opisanymi w temacie [Dodawanie paska narzędzi do okna narzędzi](../extensibility/adding-a-toolbar-to-a-tool-window.md) , aby utworzyć okno narzędzia z paskiem narzędzi.

2. W *TWTestCommandPackage. vsct* przejdź do sekcji symbole. W elemencie GuidSymbol o nazwie **guidTWTestCommandPackageCmdSet** Zadeklaruj kontroler menu, grupę kontrolerów menu i trzy elementy menu.

    ```xml
    <IDSymbol name="TestMenuController" value="0x1300" /><IDSymbol name="TestMenuControllerGroup" value="0x1060" /><IDSymbol name="cmdidMCItem1" value="0x0130" /><IDSymbol name="cmdidMCItem2" value="0x0131" /><IDSymbol name="cmdidMCItem3" value="0x0132" />
    ```

3. W sekcji menu, po ostatnim wpisie menu, zdefiniuj kontroler menu jako menu.

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

    `TextChanges`Flagi i `TextIsAnchorCommand` muszą być dołączone, aby umożliwić kontrolerowi menu odzwierciedlenie ostatniego wybranego polecenia.

4. W sekcji grupy po ostatnim wpisie grupy Dodaj grupę kontrolera menu.

    ```xml
    <Group guid="guidTWTestCommandPackageCmdSet" id="TestMenuControllerGroup" priority="0x000">
        <Parent guid="guidTWTestCommandPackageCmdSet" id="TestMenuController" />
    </Group>
    ```

    Ustawiając kontroler menu jako element nadrzędny, wszystkie polecenia umieszczane w tej grupie pojawiają się w kontrolerze menu. `priority`Atrybut zostanie pominięty, co powoduje ustawienie wartości domyślnej równej 0, ponieważ jest to jedyna grupa w kontrolerze menu.

5. W sekcji przyciski po ostatnim wpisie przycisku Dodaj element Button dla każdego z elementów menu.

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

6. W tym momencie można przyjrzeć się kontrolerowi menu. Skompiluj projekt i Rozpocznij debugowanie. Powinno być widoczne wystąpienie eksperymentalne.

   1. W menu **Widok/inne okna** Otwórz pozycję **test ToolWindow**.

   2. Kontroler menu pojawia się na pasku narzędzi w oknie narzędzi.

   3. Kliknij strzałkę po prawej stronie kontrolera menu, aby zobaczyć trzy możliwe polecenia.

      Zauważ, że po kliknięciu polecenia, tytuł kontrolera menu zmieni się, aby wyświetlić to polecenie. W następnej sekcji dodamy kod umożliwiający aktywowanie tych poleceń.

## <a name="implement-the-menu-controller-commands"></a>Implementowanie poleceń kontrolera menu

1. W *TWTestCommandPackageGuids. cs* Dodaj identyfikatory poleceń dla trzech elementów menu po istniejących identyfikatorach poleceń.

    ```csharp
    public const int cmdidMCItem1 = 0x130;
    public const int cmdidMCItem2 = 0x131;
    public const int cmdidMCItem3 = 0x132;
    ```

2. W *TWTestCommand. cs* Dodaj następujący kod w górnej części `TWTestCommand` klasy.

    ```csharp
    private int currentMCCommand; // The currently selected menu controller command
    ```

3. W konstruktorze TWTestCommand po ostatnim wywołaniu `AddCommand` metody Dodaj kod, aby skierować zdarzenia dla każdego polecenia za pomocą tych samych programów obsługi.

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

4. Dodaj procedurę obsługi zdarzeń do klasy **TWTestCommand** , aby oznaczyć wybrane polecenie jako zaznaczone.

    ```csharp
    private void OnMCItemQueryStatus(object sender, EventArgs e)
    {
        OleMenuCommand mc = sender as OleMenuCommand;
        if (null != mc)
        {
            mc.Checked = (mc.CommandID.ID == this.currentMCCommand);
        }
    }
    ```

5. Dodaj program obsługi zdarzeń, który wyświetla element MessageBox, gdy użytkownik wybierze polecenie w kontrolerze menu:

    ```csharp
    private void OnMCItemClicked(object sender, EventArgs e)
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

1. Skompiluj projekt i Rozpocznij debugowanie. Powinno być widoczne wystąpienie eksperymentalne.

2. Otwórz **test ToolWindow** w **widoku/innym menu systemu Windows** .

    Kontroler menu pojawia się na pasku narzędzi w oknie narzędzia i wyświetla **element MC o 1**.

3. Kliknij przycisk kontroler menu z lewej strony strzałki.

    Powinny pojawić się trzy elementy, pierwszy z nich jest zaznaczony i ma pole wyróżnione wokół jego ikony. Kliknij pozycję **MC element 3**.

    Zostanie wyświetlone okno dialogowe z wybranym komunikatem **menu element kontroler 3**. Zauważ, że komunikat odpowiada tekstowi na przycisku kontrolera menu. Przycisk kontroler menu wyświetla teraz **pozycję MC element 3**.

## <a name="see-also"></a>Zobacz też
- [Dodawanie paska narzędzi do okna narzędzi](../extensibility/adding-a-toolbar-to-a-tool-window.md)
- [Dodawanie paska narzędzi](../extensibility/adding-a-toolbar.md)
