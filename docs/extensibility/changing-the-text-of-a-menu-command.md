---
title: Zmiana tekstu polecenia menu | Microsoft Docs
description: Dowiedz się, jak zmienić etykietę tekstową polecenia menu za pomocą usługi IMenuCommandService, przeglądając ten przykład kodu.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- menus, changing text
- text, menus
- commands, changing text
ms.assetid: 5cb676a0-c6e2-47e5-bd2b-133dc8842e46
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: e2d812dbee833358f682b5227785c78322efe44a
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99911240"
---
# <a name="change-the-text-of-a-menu-command"></a>Zmiana tekstu polecenia menu
Poniższe kroki pokazują, jak zmienić etykietę tekstową polecenia menu za pomocą <xref:System.ComponentModel.Design.IMenuCommandService> usługi.

## <a name="changing-a-menu-command-label-with-the-imenucommandservice"></a>Zmiana etykiety polecenia menu za pomocą IMenuCommandService

1. Utwórz projekt VSIX o nazwie `MenuText` przy użyciu polecenia menu o nazwie **ChangeMenuText**. Aby uzyskać więcej informacji, zobacz [Tworzenie rozszerzenia za pomocą polecenia menu](../extensibility/creating-an-extension-with-a-menu-command.md).

2. W pliku *. vsct* Dodaj `TextChanges` flagę do polecenia menu, jak pokazano w poniższym przykładzie.

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

3. W pliku *ChangeMenuText.cs* Utwórz procedurę obsługi zdarzeń, która zostanie wywołana przed wyświetleniem polecenia menu.

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

    Możesz również zaktualizować stan polecenia menu w tej metodzie <xref:System.ComponentModel.Design.MenuCommand.Visible%2A> , zmieniając <xref:System.ComponentModel.Design.MenuCommand.Checked%2A> właściwości, i <xref:System.ComponentModel.Design.MenuCommand.Enabled%2A> w <xref:Microsoft.VisualStudio.Shell.OleMenuCommand> obiekcie.

4. W konstruktorze ChangeMenuText Zastąp pierwotne inicjowanie poleceń i kod umieszczania z kodem, który tworzy <xref:Microsoft.VisualStudio.Shell.OleMenuCommand> (a nie a `MenuCommand` ), który reprezentuje polecenie menu, dodaje <xref:Microsoft.VisualStudio.Shell.OleMenuCommand.BeforeQueryStatus> procedurę obsługi zdarzeń i nadaje polecenie menu do usługi poleceń menu.

    Oto co powinno wyglądać następująco:

    ```csharp
    private ChangeMenuText(AsyncPackage package, OleMenuCommandService commandService)
    {
        this.package = package ?? throw new ArgumentNullException(nameof(package));
        commandService = commandService ?? throw new ArgumentNullException(nameof(commandService));
        
        var menuCommandID = new CommandID(CommandSet, CommandId);
        var menuItem = new OleMenuCommand(this.Excute, menuCommandID);
        menuItem.BeforeQueryStatus += new EventHandler(OnBeforeQueryStatus);
        commandService.AddCommand(menuItem);
    }
    ```

5. Skompiluj projekt i Rozpocznij debugowanie. Pojawia się eksperymentalne wystąpienie programu Visual Studio.

6. W menu **Narzędzia** powinien pojawić się polecenie o nazwie **Invoke ChangeMenuText**.

7. Kliknij polecenie. Powinien zostać wyświetlony komunikat informujący o tym, że **MenuItemCallback** został wywołany. Po odwiedzeniu okna komunikatu powinna zostać wyświetlona nazwa polecenia w menu Narzędzia teraz **Nowy tekst**.
