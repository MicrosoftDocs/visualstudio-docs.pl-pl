---
title: Tworzenie okna narzędzia z obsługą wiele wystąpień | Microsoft Docs
description: Dowiedz się, jak zmodyfikować okno narzędzi, tak aby można było otworzyć wiele wystąpień go jednocześnie. Domyślnie w oknach narzędzi może być otwarte tylko jedno wystąpienie.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- multi
- tool windows
ms.assetid: 4a7872f1-acc9-4f43-8932-5a526b36adea
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: ce6122cbf4d6f85ab50e067fbbd643053ac4e4dd
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/25/2021
ms.locfileid: "105089358"
---
# <a name="create-a-multi-instance-tool-window"></a>Tworzenie okna narzędzia z obsługą wiele wystąpień
Możesz zaprogramować okno narzędzi, aby można było otworzyć wiele wystąpień go jednocześnie. Domyślnie w oknach narzędzi może być otwarte tylko jedno wystąpienie.

W przypadku korzystania z okna narzędzia z wieloma wystąpieniami można w tym samym czasie pokazać kilka powiązanych źródeł informacji. Na przykład można umieścić formant wielowierszowy <xref:System.Windows.Forms.TextBox> w oknie narzędzia z wieloma wystąpieniami, tak aby kilka fragmentów kodu było jednocześnie dostępnych podczas sesji programowania. Ponadto można na przykład umieścić <xref:System.Windows.Forms.DataGrid> formant i pole listy rozwijanej w oknie narzędzia z wieloma wystąpieniami, aby można było jednocześnie śledzić kilka źródeł danych w czasie rzeczywistym.

## <a name="create-a-basic-single-instance-tool-window"></a>Tworzenie podstawowego (pojedynczego wystąpienia) okna narzędziowego

1. Utwórz projekt o nazwie **MultiInstanceToolWindow** przy użyciu szablonu VSIX i Dodaj szablon elementu niestandardowego okna narzędzi o nazwie **MIToolWindow**.

    > [!NOTE]
    > Aby uzyskać więcej informacji na temat tworzenia rozszerzenia za pomocą okna narzędzi, zobacz [Tworzenie rozszerzenia przy użyciu okna narzędzi](../extensibility/creating-an-extension-with-a-tool-window.md).

## <a name="make-a-tool-window-multi-instance"></a>Tworzenie wieloskładnikowego okna narzędziowego

1. Otwórz plik *MIToolWindowPackage. cs* i Znajdź `ProvideToolWindow` atrybut. i `MultiInstances=true` parametr, jak pokazano w następującym przykładzie:

    ```csharp
    [PackageRegistration(UseManagedResourcesOnly = true)]
        [InstalledProductRegistration("#110", "#112", "1.0", IconResourceID = 400)] // Info on this package for Help/About
        [ProvideMenuResource("Menus.ctmenu", 1)]
        [ProvideToolWindow(typeof(MultiInstanceToolWindow.MIToolWindow), MultiInstances = true)]
        [Guid(MIToolWindowPackage.PackageGuidString)]
        public sealed class MIToolWindowPackage : Package
    {. . .}
    ```

2. W pliku *MIToolWindowCommand. cs* Znajdź `ShowToolWindos()` metodę. W tej metodzie należy wywołać <xref:Microsoft.VisualStudio.Shell.Package.FindToolWindow%2A> metodę i ustawić jej `create` flagę na `false` tak, aby przeprowadzili iterację przez istniejące wystąpienia okna narzędzi do momentu znalezienia dostępnego elementu `id` .

3. Aby utworzyć wystąpienie okna narzędzi, wywołaj <xref:Microsoft.VisualStudio.Shell.Package.FindToolWindow%2A> metodę i ustaw jej `id` wartość na dostępna i `create` flagę na `true` .

    Domyślnie wartość `id` parametru <xref:Microsoft.VisualStudio.Shell.Package.FindToolWindow%2A> metody to `0` . Ta wartość tworzy okno narzędzia z jednym wystąpieniem. Aby można było obsługiwać więcej niż jedno wystąpienie, każde wystąpienie musi mieć własny unikatowy `id` .

4. Wywołaj <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.Show%2A> metodę dla <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame> obiektu, który jest zwracany przez <xref:Microsoft.VisualStudio.Shell.ToolWindowPane.Frame%2A> Właściwość wystąpienia okna narzędzi.

5. Domyślnie `ShowToolWindow` Metoda, która jest tworzona przez szablon elementu okna narzędzi, tworzy okno narzędzia z jednym wystąpieniem. Poniższy przykład pokazuje, jak zmodyfikować `ShowToolWindow` metodę w celu utworzenia wielu wystąpień.

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
