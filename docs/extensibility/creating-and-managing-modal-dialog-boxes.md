---
title: Tworzenie modalnych okien dialogowych i zarządzanie nimi | Microsoft Docs
description: Dowiedz się, jak utworzyć modalne okno dialogowe w programie Visual Studio, zarówno przy użyciu DialogWindow, jak i bez użycia DialogWindow.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- dialog boxes, managing in Visual Studio
ms.assetid: 491bc0de-7dba-478c-a76b-923440e090f3
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 949f136913a30848ba13185bc699fa0bc51ac456
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99884978"
---
# <a name="create-and-manage-modal-dialog-boxes"></a>Tworzenie modalnych okien dialogowych i zarządzanie nimi
Gdy tworzysz modalne okno dialogowe w programie Visual Studio, musisz upewnić się, że okno dialogowe nadrzędne jest wyłączone podczas wyświetlania okna dialogowego, a następnie ponownie włącz okno nadrzędne po zamknięciu okna dialogowego. Jeśli tego nie zrobisz, może zostać wyświetlony komunikat o błędzie: *Microsoft Visual Studio nie może zostać zamknięty, ponieważ modalne okno dialogowe jest aktywne. Zamknij aktywne okno dialogowe i spróbuj ponownie.*

Istnieją dwa sposoby wykonania tej czynności. Zalecanym sposobem, jeśli masz okno dialogowe WPF, jest to pochodne od <xref:Microsoft.VisualStudio.PlatformUI.DialogWindow> , a następnie Wywołaj, <xref:Microsoft.VisualStudio.PlatformUI.DialogWindow.ShowModal%2A> Aby wyświetlić okno dialogowe. Jeśli to zrobisz, nie musisz zarządzać stanem modalnym okna nadrzędnego.

Jeśli okno dialogowe nie jest WPF lub z innego powodu nie można utworzyć klasy okna dialogowego z <xref:Microsoft.VisualStudio.PlatformUI.DialogWindow> , należy uzyskać nadrzędne okno dialogowe, wywołując <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.GetDialogOwnerHwnd%2A> i zarządzając stan modalny samodzielnie, przez wywołanie <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.EnableModeless%2A> metody z parametrem 0 (false) przed wyświetleniem okna dialogowego i wywołaniem metody z parametrem 1 (true) po zamknięciu okna dialogowego.

## <a name="create-a-dialog-box-derived-from-dialogwindow"></a>Utwórz okno dialogowe pochodzące z DialogWindow

1. Utwórz projekt VSIX o nazwie **OpenDialogTest** i Dodaj polecenie menu o nazwie **openDialog**. Aby uzyskać więcej informacji o tym, jak to zrobić, zobacz [Tworzenie rozszerzenia za pomocą polecenia menu](../extensibility/creating-an-extension-with-a-menu-command.md).

2. Aby użyć <xref:Microsoft.VisualStudio.PlatformUI.DialogWindow> klasy, należy dodać odwołania do następujących zestawów (na karcie struktura okna dialogowego **Dodaj odwołanie** ):

    - *'Presentationcore*

    - *Platformie docelowej*

    - *'Windowsbase*

    - *System. XAML*

3. W *openDialog.cs*, Dodaj następującą `using` instrukcję:

    ```csharp
    using Microsoft.VisualStudio.PlatformUI;
    ```

4. Zadeklaruj klasę o nazwie `TestDialogWindow` , która pochodzi od <xref:Microsoft.VisualStudio.PlatformUI.DialogWindow> :

    ```csharp
    class TestDialogWindow : DialogWindow
    {. . .}
    ```

5. Aby możliwe było zminimalizowanie i Zmaksymalizowanie okna dialogowego, ustaw <xref:Microsoft.VisualStudio.PlatformUI.DialogWindowBase.HasMaximizeButton%2A> i <xref:Microsoft.VisualStudio.PlatformUI.DialogWindowBase.HasMinimizeButton%2A> na true:

    ```csharp
    internal TestDialogWindow()
    {
        this.HasMaximizeButton = true;
        this.HasMinimizeButton = true;
    }
    ```

6. W `OpenDialog.ShowMessageBox` metodzie Zastąp istniejący kod następującym kodem:

    ```csharp
    TestDialogWindow testDialog = new TestDialogWindow();
    testDialog.ShowModal();
    ```

7. Skompiluj i uruchom aplikację. Powinno zostać wyświetlone eksperymentalne wystąpienie programu Visual Studio. W menu **Narzędzia** wystąpienia eksperymentalnego powinno zostać wyświetlone polecenie o nazwie **Invoke openDialog**. Po kliknięciu tego polecenia zostanie wyświetlone okno dialogowe. Powinno być możliwe minimalizowanie i Zmaksymalizowanie okna.

## <a name="create-and-manage-a-dialog-box-not-derived-from-dialogwindow"></a>Tworzenie okna dialogowego i zarządzanie nim, które nie pochodzi od DialogWindow

1. W przypadku tej procedury można użyć rozwiązania **OpenDialogTest** utworzonego w poprzedniej procedurze z tymi samymi odwołaniami do zestawu.

2. Dodaj następujące `using` deklaracje:

    ```csharp
    using System.Windows;
    using Microsoft.Internal.VisualStudio.PlatformUI;
    ```

3. Utwórz klasę o nazwie `TestDialogWindow2` , która pochodzi od <xref:System.Windows.Window> :

    ```csharp
    class TestDialogWindow2 : Window
    {. . .}
    ```

4. Dodaj odwołanie prywatne do <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell> :

    ```
    private IVsUIShell shell;
    ```

5. Dodaj Konstruktor, który ustawia odwołanie do <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell> :

    ```csharp
    public TestDialogWindow2(IVsUIShell uiShell)
    {
        shell = uiShell;
    }
    ```

6. W `OpenDialog.ShowMessageBox` metodzie Zastąp istniejący kod następującym kodem:

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

7. Skompiluj i uruchom aplikację. W menu **Narzędzia** powinien pojawić się polecenie o nazwie **Invoke openDialog**. Po kliknięciu tego polecenia zostanie wyświetlone okno dialogowe.
