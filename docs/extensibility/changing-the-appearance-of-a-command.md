---
title: Zmiana wyglądu polecenia | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- commands, changing appearance
- menu commands, changing appearance
- menus, changing command appearance
ms.assetid: da2474fa-f92d-4e9e-b8bf-67c61bf249c2
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 7431fa1670f6a75b69c1a1033a51975307426771
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/22/2019
ms.locfileid: "56691348"
---
# <a name="change-the-appearance-of-a-command"></a>Zmiana wyglądu polecenia
Aby przekazać opinię do użytkownika, zmiana wyglądu polecenia. Na przykład możesz polecenie będzie wyglądać inaczej, gdy jest ona niedostępna. Można wprowadzić polecenia dostępne lub niedostępne, ukryć lub pokazać je, lub sprawdź lub usuń ich zaznaczenie w menu.

Zmiana wyglądu polecenia, wykonaj jedną z następujących czynności:

- Określ odpowiednie flagi w definicji polecenia w pliku poleceń w tabeli.

- Użyj <xref:Microsoft.VisualStudio.Shell.OleMenuCommandService> usługi.

- Implementowanie <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> interfejsu i modyfikowania obiektów pierwotnych polecenia.

  Poniższe kroki pokazują jak znaleźć i zaktualizować wyglądu polecenia przy użyciu Framework pakietu zarządzanego (MPF).

### <a name="to-change-the-appearance-of-a-menu-command"></a>Zmiana wyglądu polecenia menu

1. Postępuj zgodnie z instrukcjami w [zmiana tekstu polecenia menu](../extensibility/changing-the-text-of-a-menu-command.md) utworzyć element menu o nazwie `New Text`.

2. W *ChangeMenuText.cs* plików, dodaj następującą instrukcję using:

    ```csharp
    using System.Security.Permissions;
    ```

3. W *ChangeMenuTextPackageGuids.cs* plików, Dodaj następujący wiersz:

    ```csharp
    public const string guidChangeMenuTextPackageCmdSet= "00000000-0000-0000-0000-00000000";  // get the GUID from the .vsct file
    ```

4. W *ChangeMenuText.cs* pliku, Zastąp kod w metodzie ShowMessageBox następującym kodem:

    ```csharp
    private void ShowMessageBox(object sender, EventArgs e)
    {
        var command = sender as OleMenuCommand;
        if (command.Text == "New Text")
            ChangeMyCommand(command.CommandID.ID, false);
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
        return cmdUpdated;
    }
    ```

6. Skompiluj projekt, a następnie rozpocząć debugowanie. Powinna zostać wyświetlona doświadczalnym wystąpieniu programu Visual Studio.

7. Na **narzędzia** menu, kliknij przycisk **wywołania ChangeMenuText** polecenia. W tym momencie nazwa polecenia jest **wywołania ChangeMenuText**, więc nie wywołuje program obsługi poleceń **ChangeMyCommand()**.

8. Na **narzędzia** menu powinien zostać wyświetlony **nowy tekst**. Kliknij przycisk **nowy tekst**. Polecenie powinno teraz wyszarzone.

## <a name="see-also"></a>Zobacz także
- [Polecenia, menu i paski narzędzi](../extensibility/internals/commands-menus-and-toolbars.md)
- [Jak dodać elementy interfejsu użytkownika w pakietach VSPackage](../extensibility/internals/how-vspackages-add-user-interface-elements.md)
- [Rozszerzanie menu i poleceń](../extensibility/extending-menus-and-commands.md)
- [Tabeli poleceń w usłudze Visual Studio (. Pliki Vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
