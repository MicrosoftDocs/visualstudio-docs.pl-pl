---
title: Tworzenie okien dialogowych modalnych i zarządzanie nimi | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- dialog boxes, managing in Visual Studio
ms.assetid: 491bc0de-7dba-478c-a76b-923440e090f3
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 786a2fbe2b75c51420668eb1ab6f596213d3da9b
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80739494"
---
# <a name="create-and-manage-modal-dialog-boxes"></a>Tworzenie okien dialogowych modalnych i zarządzanie nimi
Podczas tworzenia modalnego okna dialogowego w programie Visual Studio należy upewnić się, że okno nadrzędne okna dialogowego jest wyłączone podczas wyświetlania okna dialogowego, a następnie ponownie włączyć okno nadrzędne po zamknięciu okna dialogowego. Jeśli tego nie zrobisz, może pojawić się błąd: *Program Microsoft Visual Studio nie może zostać zamknięty, ponieważ modalne okno dialogowe jest aktywne. Zamknij aktywne okno dialogowe i spróbuj ponownie.*

Istnieją dwa sposoby, aby to zrobić. Zalecanym sposobem, jeśli masz okno dialogowe WPF, <xref:Microsoft.VisualStudio.PlatformUI.DialogWindow>jest wyprowadzenie go z programu , a następnie wywołanie <xref:Microsoft.VisualStudio.PlatformUI.DialogWindow.ShowModal%2A> wyświetlania okna dialogowego. Jeśli to zrobisz, nie trzeba zarządzać stanem modalnej okna nadrzędnego.

Jeśli okno dialogowe nie jest WPF, lub z innego powodu <xref:Microsoft.VisualStudio.PlatformUI.DialogWindow>nie można wyprowadzić klasy okna dialogowego <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.GetDialogOwnerHwnd%2A> z , a następnie należy <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.EnableModeless%2A> uzyskać element nadrzędny okna dialogowego, wywołując i zarządzać stan modalny samodzielnie, wywołując metodę z parametrem 0 (false) przed wyświetleniem okna dialogowego i wywołanie metody ponownie z parametrem 1 (true) po zamknięciu okna dialogowego.

## <a name="create-a-dialog-box-derived-from-dialogwindow"></a>Tworzenie okna dialogowego uzyskanego z okna dialogowego DialogWindow

1. Utwórz projekt VSIX o nazwie **OpenDialogTest** i dodaj polecenie menu o nazwie **OpenDialog**. Aby uzyskać więcej informacji na temat tego, jak to zrobić, zobacz [Tworzenie rozszerzenia za pomocą polecenia menu](../extensibility/creating-an-extension-with-a-menu-command.md).

2. Aby użyć <xref:Microsoft.VisualStudio.PlatformUI.DialogWindow> tej klasy, należy dodać odwołania do następujących zestawów (na karcie Framework w oknie dialogowym **Dodawanie odwołania):**

    - *PrezentacjaCore*

    - *PresentationFramework (Ramwork prezentacji)*

    - *Windowsbase*

    - *System.xaml*

3. W *OpenDialog.cs*dodaj następującą `using` instrukcję:

    ```csharp
    using Microsoft.VisualStudio.PlatformUI;
    ```

4. Deklaruj klasę o nazwie, `TestDialogWindow` która pochodzi od: <xref:Microsoft.VisualStudio.PlatformUI.DialogWindow>

    ```csharp
    class TestDialogWindow : DialogWindow
    {. . .}
    ```

5. Aby zminimalizować i zmaksymalizować okno dialogowe, ustaw <xref:Microsoft.VisualStudio.PlatformUI.DialogWindowBase.HasMaximizeButton%2A> i <xref:Microsoft.VisualStudio.PlatformUI.DialogWindowBase.HasMinimizeButton%2A> wartość true:

    ```csharp
    internal TestDialogWindow()
    {
        this.HasMaximizeButton = true;
        this.HasMinimizeButton = true;
    }
    ```

6. W `OpenDialog.ShowMessageBox` metodzie zastąp istniejący kod następującymi:

    ```csharp
    TestDialogWindow testDialog = new TestDialogWindow();
    testDialog.ShowModal();
    ```

7. Skompiluj i uruchom aplikację. Powinno pojawić się eksperymentalne wystąpienie programu Visual Studio. W menu **Narzędzia** wystąpienia eksperymentalnego powinno być widoczne polecenie o nazwie **Invoke OpenDialog**. Po kliknięciu tego polecenia powinno zostać wyświetlone okno dialogowe. Powinieneś być w stanie zminimalizować i zmaksymalizować okno.

## <a name="create-and-manage-a-dialog-box-not-derived-from-dialogwindow"></a>Tworzenie okna dialogowego nie pochodzące z okna dialogowego DialogWindow i zarządzanie nim

1. W tej procedurze można użyć **OpenDialogTest** rozwiązanie utworzone w poprzedniej procedurze, z tych samych odwołań do zestawu.

2. Dodaj następujące `using` deklaracje:

    ```csharp
    using System.Windows;
    using Microsoft.Internal.VisualStudio.PlatformUI;
    ```

3. Utwórz klasę `TestDialogWindow2` o nazwie, która wywodzi się z: <xref:System.Windows.Window>

    ```csharp
    class TestDialogWindow2 : Window
    {. . .}
    ```

4. Dodaj prywatne odwołanie <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell>do:

    ```
    private IVsUIShell shell;
    ```

5. Dodaj konstruktora, który <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell>ustawia odwołanie do:

    ```csharp
    public TestDialogWindow2(IVsUIShell uiShell)
    {
        shell = uiShell;
    }
    ```

6. W `OpenDialog.ShowMessageBox` metodzie zastąp istniejący kod następującymi:

    ```csharp
    IVsUIShell uiShell = (IVsUIShell)ServiceProvider.GetService(typeof(SVsUIShell));

    TestDialogWindow2 testDialog2 = new TestDialogWindow2(uiShell);
    //get the owner of this dialog
    IntPtr hwnd;
    uiShell.GetDialogOwnerHwnd(out hwnd);
    testDialog2.WindowStartupLocation = System.Windows.WindowStartupLocation.CenterOwner;
    uiShell.EnableModeless(0);
    try
    {
        WindowHelper.ShowModal(testDialog2, hwnd);
    }
    finally
    {
        // This will take place after the window is closed.
        uiShell.EnableModeless(1);
    }
    ```

7. Skompiluj i uruchom aplikację. W menu **Narzędzia** powinno być widoczne polecenie o nazwie **Invoke OpenDialog**. Po kliknięciu tego polecenia powinno zostać wyświetlone okno dialogowe.
