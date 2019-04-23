---
title: Zmiana wyglądu polecenia | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- commands, changing appearance
- menu commands, changing appearance
- menus, changing command appearance
ms.assetid: da2474fa-f92d-4e9e-b8bf-67c61bf249c2
caps.latest.revision: 24
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 4741059410e052c571d77088b9cbe109fb651642
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2019
ms.locfileid: "60095070"
---
# <a name="changing-the-appearance-of-a-command"></a>Zmiana wyglądu polecenia
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Aby przekazać opinię do użytkownika, zmiana wyglądu polecenia. Na przykład możesz polecenie będzie wyglądać inaczej, gdy jest ona niedostępna. Można wprowadzić polecenia dostępne lub niedostępne, ukryć lub pokazać je, lub sprawdź lub usuń ich zaznaczenie w menu.  
  
 Zmiana wyglądu polecenia, wykonaj jedną z następujących czynności:  
  
- Określ odpowiednie flagi w definicji polecenia w pliku poleceń w tabeli.  
  
- Użyj <xref:Microsoft.VisualStudio.Shell.OleMenuCommandService> usługi.  
  
- Implementowanie <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> interfejsu i modyfikowania obiektów pierwotnych polecenia.  
  
  Poniższe kroki pokazują jak znaleźć i zaktualizować wyglądu polecenia przy użyciu Framework pakietu zarządzanego (MPF).  
  
### <a name="to-change-the-appearance-of-a-menu-command"></a>Zmiana wyglądu polecenia menu  
  
1. Postępuj zgodnie z instrukcjami w [zmiana tekstu polecenia Menu](../extensibility/changing-the-text-of-a-menu-command.md) utworzyć element menu o nazwie `New Text`.  
  
2. W pliku ChangeMenuText.cs, dodaj następującą instrukcję using:  
  
    ```csharp  
    using System.Security.Permissions;  
    ```  
  
3. W pliku ChangeMenuTextPackageGuids.cs Dodaj następujący wiersz:  
  
    ```csharp  
    public const string guidChangeMenuTextPackageCmdSet= "00000000-0000-0000-0000-00000000";  // get the GUID from the .vsct file  
    ```  
  
4. W pliku ChangeMenuText.cs Zastąp kod w metodzie ShowMessageBox następujących czynności:  
  
    ```csharp  
    private void ShowMessageBox(object sender, EventArgs e)  
    {  
        var command = sender as OleMenuCommand;  
        if (command.Text == "New Text")  
            ChangeMyCommand(command.CommandID.ID, false);}  
    }  
    ```  
  
5. Uzyskaj polecenie, które chcesz zaktualizować z <xref:Microsoft.VisualStudio.Shell.OleMenuCommandService> obiektu, a następnie ustaw odpowiednie właściwości w obiekcie command. Na przykład poniższa metoda sprawia, że określone polecenie z poziomu polecenia pakietu VSPackage dostępne lub niedostępne. Poniższy kod sprawia, że element menu o nazwie `New Text` niedostępna po jego kliknięciu.  
  
    ```csharp  
    public bool ChangeMyCommand(int cmdID, bool enableCmd)  
    {  
        bool cmdUpdated = false;  
        var mcs = this.ServiceProvider.GetService(typeof(IMenuCommandService))  
            as OleMenuCommandService;  
        var newCmdID = new CommandID(new Guid(ChangeMenuTextPackageGuids.guidChangeMenuTextPackageCmdSet), cmdID);  
        MenuCommand mc = mcs.FindCommand(newCmdID);  
        if (mc != null)  
        {  
            mc.Enabled = enableCmd;  
            cmdUpdated = true;  
        }  
        return cmdUpdated;    }  
    }  
    ```  
  
6. Skompiluj projekt, a następnie rozpocząć debugowanie. Powinna zostać wyświetlona doświadczalnym wystąpieniu programu Visual Studio.  
  
7. Na **narzędzia** menu, kliknij przycisk **wywołania ChangeMenuText** polecenia. W tym momencie nazwa polecenia jest **wywołania ChangeMenuText**, dlatego program obsługi poleceń nie wywołuje ChangeMyCommand().  
  
8. Na **narzędzia** menu powinien zostać wyświetlony **nowy tekst**. Kliknij przycisk **nowy tekst**. Polecenie powinno teraz wyszarzone.  
  
## <a name="see-also"></a>Zobacz też  
 [Polecenia, menu i paski narzędzi](../extensibility/internals/commands-menus-and-toolbars.md)   
 [Jak dodać elementy interfejsu użytkownika w pakietach VSPackage](../extensibility/internals/how-vspackages-add-user-interface-elements.md)   
 [Rozszerzanie menu i poleceń](../extensibility/extending-menus-and-commands.md)   
 [Tabela poleceń programu Visual Studio (pliki Vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
