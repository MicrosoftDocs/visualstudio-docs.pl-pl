---
title: Zmiana tekstu polecenia Menu | Dokumentacja firmy Microsoft
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
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "68184492"
---
# <a name="changing-the-text-of-a-menu-command"></a>Zmiana tekstu polecenia menu
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Poniższe kroki pokazują jak zmienić etykietę tekstową, polecenia menu przy użyciu <xref:System.ComponentModel.Design.IMenuCommandService> usługi.  
  
## <a name="changing-a-menu-command-label-with-the-imenucommandservice"></a>Zmiana etykiety polecenia menu z IMenuCommandService  
  
1. Utwórz projekt VSIX, o nazwie `MenuText` za pomocą polecenia menu o nazwie **ChangeMenuText**. Aby uzyskać więcej informacji, zobacz [Tworzenie rozszerzenia za pomocą polecenia Menu](../extensibility/creating-an-extension-with-a-menu-command.md).  
  
2. W pliku .vstc Dodaj `TextChanges` Flaga polecenie menu, jak pokazano w poniższym przykładzie.  
  
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
  
3. W pliku ChangeMenuText.cs utworzyć program obsługi zdarzeń, która zostanie wywołana przed wyświetleniem polecenia menu.  
  
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
  
7. Kliknij polecenie. Powinieneś zobaczyć okno komunikatu ogłoszenie MenuItemCallback została wywołana. Podczas odrzucania okno komunikatu, powinien zostać wyświetlony, nazwa polecenia w menu Narzędzia jest teraz **nowy tekst**.
