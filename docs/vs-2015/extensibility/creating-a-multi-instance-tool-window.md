---
title: Tworzenie okna narzędzia obejmujące wiele wystąpień | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- multi
- tool windows
ms.assetid: 4a7872f1-acc9-4f43-8932-5a526b36adea
caps.latest.revision: 13
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 0dcdfe3f6e488514bb2ee1ca950e952b16039b42
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "63433844"
---
# <a name="creating-a-multi-instance-tool-window"></a>Tworzenie okna narzędzia o wielu wystąpieniach
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Można programować okna narzędzi, tak, aby wiele wystąpień może być otwarty jednocześnie. Domyślnie narzędzie systemu windows może mieć tylko jedno wystąpienie, Otwórz.  
  
 Korzystając z okna narzędzia obejmujące wiele wystąpień, można wyświetlić kilka powiązanych źródeł informacji w tym samym czasie. Na przykład można umieścić wiele wierszy <xref:System.Windows.Forms.TextBox> sterowania w oknie narzędzia obejmujące wiele wystąpień, co kilka fragmenty kodu są równocześnie dostępne podczas programowania sesji. Również na przykład możesz umieścić <xref:System.Windows.Forms.DataGrid> kontroli i listy rozwijanej pola w oknie narzędzia obejmujące wiele wystąpień, aby kilku źródeł danych w czasie rzeczywistym, które mogą być śledzone jednocześnie.  
  
## <a name="creating-a-basic-single-instance-tool-window"></a>Tworzenie okna narzędzia Basic (pojedynczego wystąpienia)  
  
1. Utwórz projekt o nazwie **MultiInstanceToolWindow** przy użyciu szablonu VSIX, a następnie dodaj niestandardowe narzędzie szablon elementu okno o nazwie **MIToolWindow**.  
  
    > [!NOTE]
    > Aby uzyskać więcej informacji na temat tworzenia rozszerzenia za pomocą okna narzędzi, zobacz [Tworzenie rozszerzenia za pomocą okna narzędzia](../extensibility/creating-an-extension-with-a-tool-window.md).  
  
## <a name="making-a-tool-window-multi-instance"></a>Tworzenie wielu wystąpień okna narzędzi  
  
1. Otwórz **MIToolWindowPackage.cs** plików i Znajdź `ProvideToolWindow` atrybutu. i `MultiInstances=true` parametru, jak pokazano w poniższym przykładzie.  
  
    ```csharp  
    [PackageRegistration(UseManagedResourcesOnly = true)]  
        [InstalledProductRegistration("#110", "#112", "1.0", IconResourceID = 400)] // Info on this package for Help/About  
        [ProvideMenuResource("Menus.ctmenu", 1)]  
        [ProvideToolWindow(typeof(MultiInstanceToolWindow.MIToolWindow), MultiInstances = true)]  
        [Guid(MIToolWindowPackageGuids.PackageGuidString)]  
        public sealed class MIToolWindowPackage : Package  
    {. . .}  
    ```  
  
2. W pliku MIToolWindowCommand.cs odnaleźć metody ShowToolWindos(). W przypadku tej metody należy wywołać <xref:Microsoft.VisualStudio.Shell.Package.FindToolWindow%2A> metody i ustaw jego `create` flaga `false` tak, aby jego iteracji przez istniejące wystąpienia okna narzędzia do momentu dostępne `id` zostanie znaleziony.  
  
3. Aby utworzyć wystąpienie okna narzędzi, wywołaj <xref:Microsoft.VisualStudio.Shell.Package.FindToolWindow%2A> metody i ustaw jego `id` dostępne wartości i jego `create` flaga `true`.  
  
     Domyślnie wartość `id` parametru <xref:Microsoft.VisualStudio.Shell.Package.FindToolWindow%2A> metodą jest `0`. To sprawia, że okno narzędzia jednego wystąpienia. Aby uzyskać więcej niż jedno wystąpienie będzie hostowana każde wystąpienie musi mieć własny unikatowy `id`.  
  
4. Wywołaj <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.Show%2A> metody <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame> obiektu, który jest zwracany przez <xref:Microsoft.VisualStudio.Shell.ToolWindowPane.Frame%2A> właściwości wystąpienia okna narzędzia.  
  
5. Domyślnie `ShowToolWindow` metodę, która jest tworzona przez szablon elementu okno narzędzia tworzy okno narzędzi jednego wystąpienia. Poniższy przykład przedstawia sposób modyfikowania `ShowToolWindow` metodę w celu utworzenia wielu wystąpień.  
  
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
