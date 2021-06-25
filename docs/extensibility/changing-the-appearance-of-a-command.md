---
title: Zmienianie wyglądu polecenia | Microsoft Docs
description: Dowiedz się, jak przekazać opinię, aby zmienić wygląd polecenia, na przykład udostępnić/niedostępne, ukryte/pokazane lub zaznaczone/niezaznaczone.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- commands, changing appearance
- menu commands, changing appearance
- menus, changing command appearance
ms.assetid: da2474fa-f92d-4e9e-b8bf-67c61bf249c2
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: ddeed08d7bc33b9a9ae5405876f3b28459d4eaf2
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/25/2021
ms.locfileid: "112905036"
---
# <a name="change-the-appearance-of-a-command"></a>Zmienianie wyglądu polecenia
Możesz przekazać opinię użytkownikowi, zmieniając wygląd polecenia. Możesz na przykład chcieć, aby polecenie wyglądało inaczej, gdy jest niedostępne. Polecenia można udostępnić lub niedostępne, ukryć lub pokazać albo sprawdzić lub usunąć ich zaznaczenie w menu.

Aby zmienić wygląd polecenia, wykonaj jedną z tych czynności:

- Określ odpowiednie flagi w definicji polecenia w pliku tabeli poleceń.

- Użyj <xref:Microsoft.VisualStudio.Shell.OleMenuCommandService> usługi.

- <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>Zaim implementuj interfejs i zmodyfikuj nieprzetworzone obiekty poleceń.

  Poniższe kroki pokazują, jak znaleźć i zaktualizować wygląd polecenia przy użyciu programu Managed Package Framework (MPF).

### <a name="to-change-the-appearance-of-a-menu-command"></a>Aby zmienić wygląd polecenia menu

1. Postępuj zgodnie z instrukcjami [w tece Zmienianie tekstu polecenia menu,](../extensibility/changing-the-text-of-a-menu-command.md) aby utworzyć element menu o nazwie `New Text` .

2. W pliku *ChangeMenuText.cs* dodaj następującą instrukcje using:

    ```csharp
    using System.Security.Permissions;
    ```

3. W pliku *ChangeMenuTextPackageGuids.cs* dodaj następujący wiersz:

    ```csharp
    public const string guidChangeMenuTextPackageCmdSet= "00000000-0000-0000-0000-00000000";  // get the GUID from the .vsct file
    ```

4. W pliku *ChangeMenuText.cs* zastąp kod w metodzie ShowMessageBox następującym kodem:

    ```csharp
    private void Execute(object sender, EventArgs e)
    {
        ThreadHelper.ThrowIfNotOnUIThread();
        var command = sender as OleMenuCommand;
        if (command.Text == "New Text")
            ChangeMyCommand(command.CommandID.ID, false);
    }
    ```

5. Uzyskaj polecenie, które chcesz zaktualizować z obiektu , a następnie <xref:Microsoft.VisualStudio.Shell.OleMenuCommandService> ustaw odpowiednie właściwości w obiekcie polecenia. Na przykład następująca metoda sprawia, że określone polecenie z zestawu poleceń VSPackage jest dostępne lub niedostępne. Poniższy kod sprawia, że element menu o nazwie `New Text` jest niedostępny po jego kliknięciu.

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

6. Skompilowanie projektu i rozpoczęcie debugowania. Powinno zostać wyświetlone eksperymentalne Visual Studio.

7. W menu **Narzędzia** kliknij polecenie **Wywołaj element ChangeMenuText.** W tym momencie nazwa polecenia to **Invoke ChangeMenuText**, więc program obsługi poleceń nie wywołuje **metody ChangeMyCommand()**.

8. W menu **Narzędzia** powinien być teraz wyświetlony tekst **Nowy.** Kliknij **pozycję Nowy tekst.** Polecenie powinno być teraz wyszarzone.

## <a name="see-also"></a>Zobacz też
- [Polecenia, menu i paski narzędzi](../extensibility/internals/commands-menus-and-toolbars.md)
- [Jak pakiet VSPackages dodaje elementy interfejsu użytkownika](../extensibility/internals/how-vspackages-add-user-interface-elements.md)
- [Rozszerzanie menu i poleceń](../extensibility/extending-menus-and-commands.md)
- [Visual Studio tabeli poleceń (. Vsct) Pliki](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
