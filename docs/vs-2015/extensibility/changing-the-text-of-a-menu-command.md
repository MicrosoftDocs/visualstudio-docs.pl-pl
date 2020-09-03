---
title: Zmiana tekstu polecenia menu | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- menus, changing text
- text, menus
- commands, changing text
ms.assetid: 5cb676a0-c6e2-47e5-bd2b-133dc8842e46
caps.latest.revision: 26
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: d8fd3fc01a5dd3e10e633b876b719695d6b26c18
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "68184492"
---
# <a name="changing-the-text-of-a-menu-command"></a>Zmiana tekstu polecenia menu
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Poniższe kroki pokazują, jak zmienić etykietę tekstową polecenia menu za pomocą <xref:System.ComponentModel.Design.IMenuCommandService> usługi.  
  
## <a name="changing-a-menu-command-label-with-the-imenucommandservice"></a>Zmiana etykiety polecenia menu za pomocą IMenuCommandService  
  
1. Utwórz projekt VSIX o nazwie `MenuText` przy użyciu polecenia menu o nazwie **ChangeMenuText**. Aby uzyskać więcej informacji, zobacz [Tworzenie rozszerzenia za pomocą polecenia menu](../extensibility/creating-an-extension-with-a-menu-command.md).  
  
2. W pliku. vstc Dodaj `TextChanges` flagę do polecenia menu, jak pokazano w poniższym przykładzie.  
  
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
  
3. W pliku ChangeMenuText.cs Utwórz procedurę obsługi zdarzeń, która zostanie wywołana przed wyświetleniem polecenia menu.  
  
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
  
5. Skompiluj projekt i Rozpocznij debugowanie. Pojawia się eksperymentalne wystąpienie programu Visual Studio.  
  
6. W menu **Narzędzia** powinien pojawić się polecenie o nazwie **Invoke ChangeMenuText**.  
  
7. Kliknij polecenie. Powinien zostać wyświetlony komunikat informujący o tym, że MenuItemCallback został wywołany. Po odwiedzeniu okna komunikatu powinna zostać wyświetlona nazwa polecenia w menu Narzędzia teraz **Nowy tekst**.
