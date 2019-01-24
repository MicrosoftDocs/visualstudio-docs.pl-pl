---
title: Tworzenie i zarządzanie modalne okna dialogowe | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- dialog boxes, managing in Visual Studio
ms.assetid: 491bc0de-7dba-478c-a76b-923440e090f3
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 20710f60a06c02391d467981b01627085c04a336
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54775100"
---
# <a name="creating-and-managing-modal-dialog-boxes"></a>Tworzenie modalnych okien dialogowych i zarządzanie nimi
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Podczas tworzenia modalne okno dialogowe w programie Visual Studio należy upewnić się, że okno nadrzędne, okno dialogowe jest wyłączona, gdy zostanie wyświetlone okno dialogowe, a następnie ponownie włączyć okno nadrzędne, po zamknięciu okna dialogowego. Jeśli to zrobisz, może wystąpić błąd: "Microsoft Visual Studio nie można zamknąć, ponieważ modalne okno dialogowe jest aktywne. Zamknij aktywne okno i spróbuj ponownie."  
  
 Istnieją dwa sposoby to zrobić. Zalecaną metodą, jeśli okno dialogowe WPF jest pochodzi on z <xref:Microsoft.VisualStudio.PlatformUI.DialogWindow>, a następnie wywołaj <xref:Microsoft.VisualStudio.PlatformUI.DialogWindow.ShowModal%2A> zostanie wyświetlone okno dialogowe. Jeśli to zrobisz, nie musisz zarządzać stanem modalne okno nadrzędne.  
  
 Jeśli Twoje okno dialogowe nie jest WPF lub niektóre inne przyczyny nie może pochodzić z okna dialogowego klasy z <xref:Microsoft.VisualStudio.PlatformUI.DialogWindow>, nadrzędny okna dialogowego musi uzyskać przez wywołanie metody <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.GetDialogOwnerHwnd%2A> i zarządzanie nimi stan modalny samodzielnie, wywołując <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.EnableModeless%2A> metody za pomocą Parametr 0 (false) przed wyświetleniem okna dialogowego i wywołanie metody ponownie, podając parametr 1 (PRAWDA), po zamknięciu okna dialogowego.  
  
## <a name="creating-a-dialog-box-derived-from-dialogwindow"></a>Tworzenie okna dialogowego pochodną DialogWindow  
  
1.  Utwórz projekt VSIX, o nazwie **OpenDialogTest** i dodać polecenie menu o nazwie **OpenDialog**. Aby uzyskać więcej informacji na temat jak to zrobić, zobacz [Tworzenie rozszerzenia za pomocą polecenia Menu](../extensibility/creating-an-extension-with-a-menu-command.md).  
  
2.  Aby użyć <xref:Microsoft.VisualStudio.PlatformUI.DialogWindow> klasy, należy dodać odwołania do następujących zestawów (na karcie Framework **Dodaj odwołanie** okno dialogowe):  
  
    -   PresentationCore  
  
    -   PresentationFramework  
  
    -   WindowsBase  
  
    -   System.Xaml  
  
3.  W OpenDialog.cs, Dodaj następujący kod `using` instrukcji:  
  
    ```csharp  
    using Microsoft.VisualStudio.PlatformUI;  
    ```  
  
4.  Zadeklaruj klasę o nazwie **TestDialogWindow** który pochodzi od klasy <xref:Microsoft.VisualStudio.PlatformUI.DialogWindow>:  
  
    ```csharp  
    class TestDialogWindow : DialogWindow  
    {. . .}  
    ```  
  
5.  Aby można było zminimalizowanie i zmaksymalizuj okno dialogowe, należy ustawić <xref:Microsoft.VisualStudio.PlatformUI.DialogWindowBase.HasMaximizeButton%2A> i <xref:Microsoft.VisualStudio.PlatformUI.DialogWindowBase.HasMinimizeButton%2A> na wartość true:  
  
    ```csharp  
    internal TestDialogWindow()  
    {  
        this.HasMaximizeButton = true;  
        this.HasMinimizeButton = true;  
    }  
    ```  
  
6.  W **OpenDialog.ShowMessageBox** metody, Zastąp istniejący kod następującym kodem:  
  
    ```csharp  
    TestDialogWindow testDialog = new TestDialogWindow();  
    testDialog.ShowModal();  
    ```  
  
7.  Skompiluj i uruchom aplikację. Powinna zostać wyświetlona doświadczalnym wystąpieniu programu Visual Studio. Na **narzędzia** menu w eksperymentalnym wystąpieniu powinien zostać wyświetlony polecenie o nazwie **wywołania OpenDialog**. Po kliknięciu tego polecenia, powinno zostać wyświetlone okno dialogowe. Można zminimalizować i zmaksymalizuj okno.  
  
## <a name="creating-and-managing-a-dialog-box-not-derived-from-dialogwindow"></a>Tworzenie i zarządzanie nimi nie pochodzi od DialogWindow okno dialogowe  
  
1.  Do wykonania tej procedury, można użyć **OpenDialogTest** rozwiązanie utworzone w poprzedniej procedurze, za pomocą tego samego odwołania do zestawu.  
  
2.  Dodaj następujący kod `using` deklaracje:  
  
    ```csharp  
    using System.Windows;  
    using Microsoft.Internal.VisualStudio.PlatformUI;  
    ```  
  
3.  Utwórz klasę o nazwie **TestDialogWindow2** który pochodzi od klasy <xref:System.Windows.Window>:  
  
    ```csharp  
    class TestDialogWindow2 : Window  
    {. . .}  
    ```  
  
4.  Dodaj odwołanie prywatnych do <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell>:  
  
    ```  
    private IVsUIShell shell;  
    ```  
  
5.  Dodaj Konstruktor, który ustawia odwołanie <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell>:  
  
    ```csharp  
    public TestDialogWindow2(IVsUIShell uiShell)  
    {  
        shell = uiShell;  
    }  
    ```  
  
6.  W **OpenDialog.ShowMessageBox** metody, Zastąp istniejący kod następującym kodem:  
  
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
  
7.  Skompiluj i uruchom aplikację. Na **narzędzia** menu powinien zostać wyświetlony polecenie o nazwie **wywołania OpenDialog**. Po kliknięciu tego polecenia, powinno zostać wyświetlone okno dialogowe.
