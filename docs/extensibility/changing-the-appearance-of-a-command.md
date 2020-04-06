---
title: Zmiana wyglądu polecenia | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- commands, changing appearance
- menu commands, changing appearance
- menus, changing command appearance
ms.assetid: da2474fa-f92d-4e9e-b8bf-67c61bf249c2
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 653f516dda89f4895b8d19d77f7f49bf9c6aa45b
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80739850"
---
# <a name="change-the-appearance-of-a-command"></a>Zmienianie wyglądu polecenia
Możesz przekazać opinię użytkownikowi, zmieniając wygląd polecenia. Na przykład może być polecenie wyglądać inaczej, gdy jest niedostępny. Możesz udostępnić lub niedostępne polecenia, ukryć lub pokazać je, lub zaznaczyć lub odznaczyć je w menu.

Aby zmienić wygląd polecenia, wykonaj jedną z następujących czynności:

- Określ odpowiednie flagi w definicji polecenia w pliku tabeli poleceń.

- Skorzystaj <xref:Microsoft.VisualStudio.Shell.OleMenuCommandService> z usługi.

- Zaimplementuj <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> interfejs i zmodyfikuj nieprzetworzone obiekty poleceń.

  Poniższe kroki pokazują, jak znaleźć i zaktualizować wygląd polecenia przy użyciu struktury pakietu zarządzanego (MPF).

### <a name="to-change-the-appearance-of-a-menu-command"></a>Aby zmienić wygląd polecenia menu

1. Postępuj zgodnie z instrukcjami w pozycji Zmień tekst `New Text`polecenia [menu,](../extensibility/changing-the-text-of-a-menu-command.md) aby utworzyć element menu o nazwie .

2. W pliku *ChangeMenuText.cs* dodaj następującą instrukcję za pomocą:

    ```csharp
    using System.Security.Permissions;
    ```

3. W pliku *ChangeMenuTextPackageGuids.cs* dodaj następujący wiersz:

    ```csharp
    public const string guidChangeMenuTextPackageCmdSet= "00000000-0000-0000-0000-00000000";  // get the GUID from the .vsct file
    ```

4. W pliku *ChangeMenuText.cs* zastąp kod w metodzie ShowMessageBox następującymi:

    ```csharp
    private void ShowMessageBox(object sender, EventArgs e)
    {
        var command = sender as OleMenuCommand;
        if (command.Text == "New Text")
            ChangeMyCommand(command.CommandID.ID, false);
    }
    ```

5. Uzyskaj polecenie, które chcesz zaktualizować <xref:Microsoft.VisualStudio.Shell.OleMenuCommandService> z obiektu, a następnie ustaw odpowiednie właściwości obiektu polecenia. Na przykład następująca metoda sprawia, że określone polecenie z zestawu poleceń VSPackage jest dostępne lub niedostępne. Poniższy kod sprawia, `New Text` że element menu o nazwie niedostępne po kliknięciu.

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
        return cmdUpdated;
    }
    ```

6. Skompiluj projekt i rozpocznij debugowanie. Powinno pojawić się eksperymentalne wystąpienie programu Visual Studio.

7. W menu **Narzędzia** kliknij polecenie **Wywołaj polecenie ChangeMenuText.** W tym momencie nazwa polecenia to **Invoke ChangeMenuText**, więc program obsługi poleceń nie wywołuje **changemycommand().**

8. W menu **Narzędzia** powinieneś teraz zobaczyć **nowy tekst**. Kliknij **pozycję Nowy tekst**. Polecenie powinno być teraz wyszarzone.

## <a name="see-also"></a>Zobacz też
- [Polecenia, menu i paski narzędzi](../extensibility/internals/commands-menus-and-toolbars.md)
- [Jak vspackages dodać elementy interfejsu użytkownika](../extensibility/internals/how-vspackages-add-user-interface-elements.md)
- [Rozszerzanie menu i poleceń](../extensibility/extending-menus-and-commands.md)
- [Tabela poleceń programu Visual Studio (. Vsct) Pliki](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
