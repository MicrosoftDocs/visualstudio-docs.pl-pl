---
title: Tworzenie okna narzędzia obejmujące wiele wystąpień | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- multi
- tool windows
ms.assetid: 4a7872f1-acc9-4f43-8932-5a526b36adea
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 0b92fefd555b58852a5f6c3d8afc57f159d493dc
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/25/2019
ms.locfileid: "54916658"
---
# <a name="create-a-multi-instance-tool-window"></a>Utworzenie okna narzędzia obejmujące wiele wystąpień
Można programować okna narzędzi, tak, aby wiele wystąpień może być otwarty jednocześnie. Domyślnie narzędzie systemu windows może mieć tylko jedno wystąpienie, Otwórz.  
  
 Korzystając z okna narzędzia obejmujące wiele wystąpień, można wyświetlić kilka powiązanych źródeł informacji w tym samym czasie. Na przykład można umieścić wiele wierszy <xref:System.Windows.Forms.TextBox> sterowania w oknie narzędzia obejmujące wiele wystąpień, co kilka fragmenty kodu są równocześnie dostępne podczas programowania sesji. Ponadto, na przykład możesz umieścić <xref:System.Windows.Forms.DataGrid> kontroli i listy rozwijanej pola w oknie narzędzia obejmujące wiele wystąpień, aby kilku źródeł danych w czasie rzeczywistym, które mogą być śledzone jednocześnie.  
  
## <a name="create-a-basic-single-instance-tool-window"></a>Utwórz okno podstawowe narzędzie (pojedynczego wystąpienia)  
  
1.  Utwórz projekt o nazwie **MultiInstanceToolWindow** przy użyciu szablonu VSIX, a następnie dodaj niestandardowe narzędzie szablon elementu okno o nazwie **MIToolWindow**.  
  
    > [!NOTE]
    >  Aby uzyskać więcej informacji na temat tworzenia rozszerzenia za pomocą okna narzędzi, zobacz [Tworzenie rozszerzenia za pomocą okna narzędzia](../extensibility/creating-an-extension-with-a-tool-window.md).  
  
## <a name="make-a-tool-window-multi-instance"></a>Wystąpienie wielu okna narzędzi  
  
1.  Otwórz *MIToolWindowPackage.cs* plików i Znajdź `ProvideToolWindow` atrybutu. i `MultiInstances=true` parametru, jak pokazano w poniższym przykładzie:  
  
    ```csharp  
    [PackageRegistration(UseManagedResourcesOnly = true)]  
        [InstalledProductRegistration("#110", "#112", "1.0", IconResourceID = 400)] // Info on this package for Help/About  
        [ProvideMenuResource("Menus.ctmenu", 1)]  
        [ProvideToolWindow(typeof(MultiInstanceToolWindow.MIToolWindow), MultiInstances = true)]  
        [Guid(MIToolWindowPackage.PackageGuidString)]  
        public sealed class MIToolWindowPackage : Package  
    {. . .}  
    ```  
  
2.  W *MIToolWindowCommand.cs* plików, Znajdź `ShowToolWindos()` metody. W przypadku tej metody należy wywołać <xref:Microsoft.VisualStudio.Shell.Package.FindToolWindow%2A> metody i ustaw jego `create` flaga `false` tak, aby jego iteracji przez istniejące wystąpienia okna narzędzia do momentu dostępne `id` zostanie znaleziony.  
  
3.  Aby utworzyć wystąpienie okna narzędzi, wywołaj <xref:Microsoft.VisualStudio.Shell.Package.FindToolWindow%2A> metody i ustaw jego `id` dostępne wartości i jego `create` flaga `true`.  
  
     Domyślnie wartość `id` parametru <xref:Microsoft.VisualStudio.Shell.Package.FindToolWindow%2A> metodą jest `0`. Ta wartość sprawia, że okno narzędzia jednego wystąpienia. Aby uzyskać więcej niż jedno wystąpienie będzie hostowana każde wystąpienie musi mieć własny unikatowy `id`.  
  
4.  Wywołaj <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.Show%2A> metody <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame> obiektu, który jest zwracany przez <xref:Microsoft.VisualStudio.Shell.ToolWindowPane.Frame%2A> właściwości wystąpienia okna narzędzia.  
  
5.  Domyślnie `ShowToolWindow` metodę, która jest tworzona przez szablon elementu okno narzędzia tworzy okno narzędzi jednego wystąpienia. Poniższy przykład przedstawia sposób modyfikowania `ShowToolWindow` metodę w celu utworzenia wielu wystąpień.  
  
    ```csharp  
    private void ShowToolWindow(object sender, EventArgs e)  
    {  
        for (int i = 0; i < 10; i++)  
        {  
            ToolWindowPane window = this.package.FindToolWindow(typeof(MIToolWindow), i, false);  
            if (window == null)  
            {  
                // Create the window with the first free ID.   
                window = (ToolWindowPane)this.package.FindToolWindow(typeof(MIToolWindow), i, true);  
                if ((null == window) || (null == window.Frame))  
                {  
                    throw new NotSupportedException("Cannot create tool window");  
                }  
  
            IVsWindowFrame windowFrame = (IVsWindowFrame)window.Frame;  
            Microsoft.VisualStudio.ErrorHandler.ThrowOnFailure(windowFrame.Show());  
            break;  
            }  
        }  
    }  
    ```