---
title: Tworzenie okna narzędzia z wieloma wystąpieniami | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- multi
- tool windows
ms.assetid: 4a7872f1-acc9-4f43-8932-5a526b36adea
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 33585f623f846e16200d430ad2c886fe0874b537
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80739624"
---
# <a name="create-a-multi-instance-tool-window"></a>Tworzenie okna narzędzia z wieloma wystąpieniami
Okno narzędzia można zaprogramować, tak aby można było jednocześnie otworzyć wiele jego wystąpień. Domyślnie okna narzędzi mogą mieć tylko jedno wystąpienie otwarte.

Korzystając z okna narzędzia z wieloma wystąpieniami, można wyświetlić kilka powiązanych źródeł informacji w tym samym czasie. Na przykład można umieścić formant <xref:System.Windows.Forms.TextBox> wielowierszowy w oknie narzędzia wielu wystąpień, tak aby kilka fragmentów kodu były jednocześnie dostępne podczas sesji programowania. Ponadto na przykład można umieścić <xref:System.Windows.Forms.DataGrid> formant i pole listy rozwijanej w oknie narzędzia wielu wystąpień, dzięki czemu można jednocześnie śledzić kilka źródeł danych w czasie rzeczywistym.

## <a name="create-a-basic-single-instance-tool-window"></a>Tworzenie okna narzędzia podstawowego (pojedynczego wystąpienia)

1. Utwórz projekt o nazwie **MultiInstanceToolWindow** przy użyciu szablonu VSIX i dodaj niestandardowy szablon elementu okna narzędzia o nazwie **MIToolWindow**.

    > [!NOTE]
    > Aby uzyskać więcej informacji na temat tworzenia rozszerzenia z oknem narzędzia, zobacz [Tworzenie rozszerzenia z oknem narzędzia](../extensibility/creating-an-extension-with-a-tool-window.md).

## <a name="make-a-tool-window-multi-instance"></a>1.

1. Otwórz plik *MIToolWindowPackage.cs* i znajdź `ProvideToolWindow` atrybut. i `MultiInstances=true` parametr, jak pokazano w poniższym przykładzie:

    ```csharp
    [PackageRegistration(UseManagedResourcesOnly = true)]
        [InstalledProductRegistration("#110", "#112", "1.0", IconResourceID = 400)] // Info on this package for Help/About
        [ProvideMenuResource("Menus.ctmenu", 1)]
        [ProvideToolWindow(typeof(MultiInstanceToolWindow.MIToolWindow), MultiInstances = true)]
        [Guid(MIToolWindowPackage.PackageGuidString)]
        public sealed class MIToolWindowPackage : Package
    {. . .}
    ```

2. W pliku *MIToolWindowCommand.cs* znajdź `ShowToolWindos()` metodę. W tej metodzie <xref:Microsoft.VisualStudio.Shell.Package.FindToolWindow%2A> wywołać `create` metodę `false` i ustawić jego flagę, aby iterować `id` za pośrednictwem istniejących wystąpień okna narzędzia, dopóki nie zostanie znaleziony dostępny.

3. Aby utworzyć wystąpienie okna <xref:Microsoft.VisualStudio.Shell.Package.FindToolWindow%2A> narzędzia, należy `id` wywołać metodę `create` i `true`ustawić jej wartość na dostępną, a flagę na .

    Domyślnie wartość parametru `id` <xref:Microsoft.VisualStudio.Shell.Package.FindToolWindow%2A> metody jest `0`. Ta wartość tworzy okno narzędzia pojedynczego wystąpienia. Aby więcej niż jedno wystąpienie było hostowane, `id`każde wystąpienie musi mieć swój własny unikatowy .

4. Wywołanie <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.Show%2A> metody <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame> na obiekcie, <xref:Microsoft.VisualStudio.Shell.ToolWindowPane.Frame%2A> który jest zwracany przez właściwość wystąpienia okna narzędzia.

5. Domyślnie metoda `ShowToolWindow` tworzona przez szablon elementu okna narzędzia tworzy okno narzędzia pojedynczego wystąpienia. W poniższym przykładzie `ShowToolWindow` pokazano, jak zmodyfikować metodę tworzenia wielu wystąpień.

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
