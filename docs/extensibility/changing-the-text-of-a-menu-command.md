---
title: Zmiana tekstu polecenia Menu | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- menus, changing text
- text, menus
- commands, changing text
ms.assetid: 5cb676a0-c6e2-47e5-bd2b-133dc8842e46
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 92e06345164b9ad147c6ba204773efaa7180b943
ms.sourcegitcommit: 752f03977f45169585e407ef719450dbe219b7fc
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/15/2019
ms.locfileid: "56315862"
---
# <a name="change-the-text-of-a-menu-command"></a>Zmiana tekstu polecenia menu
Poniższe kroki pokazują jak zmienić etykietę tekstową, polecenia menu przy użyciu <xref:System.ComponentModel.Design.IMenuCommandService> usługi.

## <a name="changing-a-menu-command-label-with-the-imenucommandservice"></a>Zmiana etykiety polecenia menu z IMenuCommandService

1. Utwórz projekt VSIX, o nazwie `MenuText` za pomocą polecenia menu o nazwie **ChangeMenuText**. Aby uzyskać więcej informacji, zobacz [Tworzenie rozszerzenia za pomocą polecenia menu](../extensibility/creating-an-extension-with-a-menu-command.md).

2. W *vsct* Dodaj `TextChanges` Flaga polecenie menu, jak pokazano w poniższym przykładzie.

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

3. W *ChangeMenuText.cs* plików, Tworzenie procedury obsługi zdarzeń, która zostanie wywołana przed wyświetleniem polecenia menu.

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

    Możesz także zaktualizować stan polecenia menu, w przypadku tej metody, zmieniając <xref:System.ComponentModel.Design.MenuCommand.Visible%2A>, <xref:System.ComponentModel.Design.MenuCommand.Checked%2A>, i <xref:System.ComponentModel.Design.MenuCommand.Enabled%2A> właściwości <xref:Microsoft.VisualStudio.Shell.OleMenuCommand> obiektu.

4. W Konstruktorze ChangeMenuText Zamień oryginalny kod inicjowania i rozmieszczenie polecenia kod, który tworzy <xref:Microsoft.VisualStudio.Shell.OleMenuCommand> (zamiast `MenuCommand`) który reprezentuje polecenie menu, dodaje <xref:Microsoft.VisualStudio.Shell.OleMenuCommand.BeforeQueryStatus> procedura obsługi zdarzeń oraz zapewnia menu polecenie usługi polecenia menu.

    Oto, co powinno to wyglądać:

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

5. Skompiluj projekt, a następnie rozpocząć debugowanie. Pojawi się doświadczalnym wystąpieniu programu Visual Studio.

6. Na **narzędzia** menu powinien zostać wyświetlony polecenie o nazwie **wywołania ChangeMenuText**.

7. Kliknij polecenie. Powinien zostać wyświetlony okno komunikatu, który ogłoszenie **MenuItemCallback** została wywołana. Podczas odrzucania okno komunikatu, powinien zostać wyświetlony, nazwa polecenia w menu Narzędzia jest teraz **nowy tekst**.
