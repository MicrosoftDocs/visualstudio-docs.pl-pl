---
title: Zmienianie tekstu polecenia menu | Microsoft Docs
description: Dowiedz się, jak zmienić etykietę tekstową polecenia menu przy użyciu usługi IMenuCommandService, przeglądając ten przykład kodu.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- menus, changing text
- text, menus
- commands, changing text
ms.assetid: 5cb676a0-c6e2-47e5-bd2b-133dc8842e46
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 541acf1bcf448541fe6c440eb2aada687cfbe0e9
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/25/2021
ms.locfileid: "112904994"
---
# <a name="change-the-text-of-a-menu-command"></a>Zmienianie tekstu polecenia menu
Poniższe kroki pokazują, jak zmienić etykietę tekstową polecenia menu przy użyciu <xref:System.ComponentModel.Design.IMenuCommandService> usługi .

## <a name="changing-a-menu-command-label-with-the-imenucommandservice"></a>Zmienianie etykiety polecenia menu za pomocą elementu IMenuCommandService

1. Utwórz projekt VSIX o nazwie `MenuText` za pomocą polecenia menu o nazwie **ChangeMenuText**. Aby uzyskać więcej informacji, zobacz Create an extension with a menu command (Tworzenie [rozszerzenia za pomocą polecenia menu).](../extensibility/creating-an-extension-with-a-menu-command.md)

2. W *pliku .vsct* dodaj `TextChanges` flagę do polecenia menu, jak pokazano w poniższym przykładzie.

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

3. W pliku *ChangeMenuText.cs* utwórz program obsługi zdarzeń, który zostanie wywołany przed wyświetlonym poleceniem menu.

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

    Możesz również zaktualizować stan polecenia menu w tej metodzie, zmieniając właściwości <xref:System.ComponentModel.Design.MenuCommand.Visible%2A> <xref:System.ComponentModel.Design.MenuCommand.Checked%2A> , i obiektu <xref:System.ComponentModel.Design.MenuCommand.Enabled%2A> <xref:Microsoft.VisualStudio.Shell.OleMenuCommand> .

4. W konstruktorze ChangeMenuText zastąp oryginalny kod inicjowania i umieszczania polecenia kodem, który tworzy (a nie ) element reprezentujący polecenie menu, dodaje program obsługi zdarzeń i udostępnia polecenie menu do <xref:Microsoft.VisualStudio.Shell.OleMenuCommand> `MenuCommand` usługi poleceń <xref:Microsoft.VisualStudio.Shell.OleMenuCommand.BeforeQueryStatus> menu.

    Oto jak powinno to wyglądać:

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

5. Skompilowanie projektu i rozpoczęcie debugowania. Zostanie wyświetlone eksperymentalne wystąpienie Visual Studio.

6. W menu **Narzędzia** powinno zostać wyświetlony polecenie o nazwie **Invoke ChangeMenuText**.

7. Kliknij polecenie . Powinno zostać wyświetlony okno komunikatu z komunikatem, że został wywołany **element MenuItemCallback.** Po odrzuć okno komunikatu powinna być widać, że nazwa polecenia w menu Narzędzia to teraz **Nowy tekst.**
