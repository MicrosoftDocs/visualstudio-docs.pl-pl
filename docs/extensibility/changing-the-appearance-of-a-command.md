---
title: Zmiana wyglądu polecenia | Microsoft Docs
description: Dowiedz się, w jaki sposób można przekazać opinię dotyczącą zmiany wyglądu polecenia, na przykład udostępnienia poleceń/niedostępności, ukrycia/wyświetlenia lub zaznaczania/niezaznaczania.
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: 0f79ac7873a1746e0b14db51ba864e94f6bbfa1e
ms.sourcegitcommit: 5027eb5c95e1d2da6d08d208fd6883819ef52d05
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/20/2020
ms.locfileid: "94974412"
---
# <a name="change-the-appearance-of-a-command"></a>Zmiana wyglądu polecenia
Możesz przekazać użytkownikowi informacje zwrotne, zmieniając wygląd polecenia. Na przykład możesz chcieć, aby polecenie wyglądało inaczej, gdy jest niedostępne. Polecenia mogą być dostępne lub niedostępne, ukrywane lub wyświetlane lub zaznaczając je w menu.

Aby zmienić wygląd polecenia, wykonaj jedną z następujących czynności:

- Określ odpowiednie flagi w definicji polecenia w pliku tabeli poleceń.

- Użyj <xref:Microsoft.VisualStudio.Shell.OleMenuCommandService> usługi.

- Zaimplementuj <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> interfejs i zmodyfikuj pierwotne obiekty poleceń.

  Poniższe kroki pokazują, jak znaleźć i zaktualizować wygląd polecenia przy użyciu struktury pakietu zarządzanego (MPF).

### <a name="to-change-the-appearance-of-a-menu-command"></a>Aby zmienić wygląd polecenia menu

1. Postępuj zgodnie z instrukcjami w [części Zmień tekst polecenia menu](../extensibility/changing-the-text-of-a-menu-command.md) , aby utworzyć element menu o nazwie `New Text` .

2. W pliku *ChangeMenuText.cs* Dodaj następującą instrukcję using:

    ```csharp
    using System.Security.Permissions;
    ```

3. W pliku *ChangeMenuTextPackageGuids.cs* Dodaj następujący wiersz:

    ```csharp
    public const string guidChangeMenuTextPackageCmdSet= "00000000-0000-0000-0000-00000000";  // get the GUID from the .vsct file
    ```

4. W pliku *ChangeMenuText.cs* Zastąp kod w metodzie ShowMessageBox następującym:

    ```csharp
    private void Execute(object sender, EventArgs e)
    {
        ThreadHelper.ThrowIfNotOnUIThread();
        var command = sender as OleMenuCommand;
        if (command.Text == "New Text")
            ChangeMyCommand(command.CommandID.ID, false);
    }
    ```

5. Uzyskaj polecenie, które chcesz zaktualizować z <xref:Microsoft.VisualStudio.Shell.OleMenuCommandService> obiektu, a następnie ustaw odpowiednie właściwości w obiekcie Command. Na przykład Poniższa metoda sprawia, że określone polecenie z zestawu poleceń pakietu VSPackage jest dostępne lub niedostępne. Poniższy kod sprawia, że element menu o nazwie `New Text` niedostępne po kliknięciu.

    ```csharp
    public bool ChangeMyCommand(int cmdID, bool enableCmd)
    {
        bool cmdUpdated = false;
        var mcs = this.package.GetService<IMenuCommandService, OleMenuCommandService>();
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

6. Skompiluj projekt i Rozpocznij debugowanie. Powinno zostać wyświetlone eksperymentalne wystąpienie programu Visual Studio.

7. W menu **Narzędzia** kliknij polecenie **Wywołaj ChangeMenuText** . W tym momencie nazwa polecenia jest wywoływana **ChangeMenuText**, więc procedura obsługi poleceń nie wywołuje **ChangeMyCommand ()**.

8. W menu **Narzędzia** powinien pojawić się **Nowy tekst**. Kliknij przycisk **Nowy tekst**. Polecenie powinno teraz być wyszarzone.

## <a name="see-also"></a>Zobacz także
- [Polecenia, menu i paski narzędzi](../extensibility/internals/commands-menus-and-toolbars.md)
- [Jak pakietów VSPackage Dodawanie elementów interfejsu użytkownika](../extensibility/internals/how-vspackages-add-user-interface-elements.md)
- [Rozszerzanie menu i poleceń](../extensibility/extending-menus-and-commands.md)
- [Tabela poleceń programu Visual Studio (. Vsct) — pliki](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
