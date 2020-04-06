---
title: Zmiana tekstu polecenia menu | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- menus, changing text
- text, menus
- commands, changing text
ms.assetid: 5cb676a0-c6e2-47e5-bd2b-133dc8842e46
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: ff6af7bdd64342e86201af79dbe5c7968b247d6b
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80739845"
---
# <a name="change-the-text-of-a-menu-command"></a>Zmienianie tekstu polecenia menu
Poniższe kroki pokazują, jak zmienić etykietę tekstową polecenia menu za pomocą <xref:System.ComponentModel.Design.IMenuCommandService> usługi.

## <a name="changing-a-menu-command-label-with-the-imenucommandservice"></a>Zmienianie etykiety polecenia menu za pomocą usługi IMenuCommandService

1. Utwórz projekt VSIX o nazwie `MenuText` polecenie menu o nazwie **ChangeMenuText**. Aby uzyskać więcej informacji, zobacz [Tworzenie rozszerzenia za pomocą polecenia menu](../extensibility/creating-an-extension-with-a-menu-command.md).

2. W pliku *vsct* dodaj `TextChanges` flagę do polecenia menu, jak pokazano w poniższym przykładzie.

    ```xml
    <Button guid="guidChangeMenuTextPackageCmdSet" id="ChangeMenuTextId" priority="0x0100" type="Button">
        <Parent guid="guidChangeMenuTextPackageCmdSet" id="MyMenuGroup" />
        <Icon guid="guidImages" id="bmpPic1" />
        <CommandFlag>TextChanges</CommandFlag>
        <Strings>
            <ButtonText>Invoke ChangeMenuText</ButtonText>
        </Strings>
    </Button>
    ```

3. W pliku *ChangeMenuText.cs* utwórz program obsługi zdarzeń, który zostanie wywołany przed wyświetleniem polecenia menu.

    ```csharp
    private void OnBeforeQueryStatus(object sender, EventArgs e)
    {
        var myCommand = sender as OleMenuCommand;
        if (null != myCommand)
        {
            myCommand.Text = "New Text";
        }
    }
    ```

    Stan polecenia menu w tej metodzie można również <xref:System.ComponentModel.Design.MenuCommand.Visible%2A> <xref:System.ComponentModel.Design.MenuCommand.Checked%2A>zaktualizować, <xref:System.ComponentModel.Design.MenuCommand.Enabled%2A> zmieniając właściwości <xref:Microsoft.VisualStudio.Shell.OleMenuCommand> obiektu i obiektu.

4. W konstruktorze ChangeMenuText zastąp oryginalny kod inicjowania polecenia `MenuCommand`i umieszczania kodem, <xref:Microsoft.VisualStudio.Shell.OleMenuCommand.BeforeQueryStatus> który tworzy <xref:Microsoft.VisualStudio.Shell.OleMenuCommand> (a), który reprezentuje polecenie menu, dodaje program obsługi zdarzeń i nadaje polecenie menu do usługi polecenia menu.

    Oto jak to powinno wyglądać:

    ```csharp
    private ChangeMenuText(Package package)
    {
        if (package == null)
        {
            throw new ArgumentNullException(nameof(package));
        }

        this.package = package;

        OleMenuCommandService commandService = this.ServiceProvider.GetService(typeof(IMenuCommandService)) as OleMenuCommandService;
        if (commandService != null)
        {
            CommandID menuCommandID = new CommandID(MenuGroup, CommandId);
            EventHandler eventHandler = this.ShowMessageBox;
            OleMenuCommand menuItem = new OleMenuCommand(ShowMessageBox, menuCommandID);
            menuItem.BeforeQueryStatus +=
                new EventHandler(OnBeforeQueryStatus);
            commandService.AddCommand(menuItem);
        }
    }
    ```

5. Skompiluj projekt i rozpocznij debugowanie. Pojawi się eksperymentalne wystąpienie programu Visual Studio.

6. W menu **Narzędzia** powinno być widoczne polecenie o nazwie **Invoke ChangeMenuText**.

7. Kliknij polecenie. Powinno zostać wyświetlone okno komunikatu z informacją, że **MenuItemCallback** został wywołany. Po odrzuceniu okna komunikatu powinna zostać wyświetlna nazwa polecenia w menu Narzędzia to teraz **Nowy tekst**.
