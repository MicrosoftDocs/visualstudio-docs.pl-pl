---
title: Pobieranie właściwości projektu | Dokumentacja firmy Microsoft
ms.date: 3/16/2019
ms.topic: conceptual
helpviewer_keywords:
- project properties, displaying in tool window
- tool windows, displaying project properties
ms.assetid: 96ba07ca-0811-4013-8602-12550ac4ba79
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 7f766be25015081338b887a5b08413e77f5f17f9
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/29/2019
ms.locfileid: "66342528"
---
# <a name="get-project-properties"></a>Uzyskiwanie właściwości projektu

Ten poradnik pokazuje jak Wyświetla właściwości projektu w oknie narzędzi.

## <a name="prerequisites"></a>Wymagania wstępne

Począwszy od programu Visual Studio 2015, możesz nie należy instalować programu Visual Studio SDK z Centrum pobierania. Jest dołączony jako opcjonalna funkcja w Instalatorze programu Visual Studio. Możesz także zainstalować zestaw SDK programu VS później. Aby uzyskać więcej informacji, zobacz [instalacji programu Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).

### <a name="to-create-a-vsix-project-and-add-a-tool-window"></a>Aby utworzyć projekt VSIX i dodać okna narzędzi

1. Każde rozszerzenie programu Visual Studio rozpoczyna się od projektu wdrożenia VSIX, który będzie zawierać zasoby rozszerzenia. Tworzenie [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] projektu VSIX, o nazwie `ProjectPropertiesExtension`. Można znaleźć szablonu projektu VSIX w **nowy projekt** okna dialogowego, wyszukując pozycję "vsix".

2. Dodawanie okna narzędzi, dodając szablon elementu niestandardowego okna narzędzi o nazwie `ProjectPropertiesToolWindow`. W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy węzeł projektu i wybierz **Dodaj** > **nowy element**. W **okna dialogowego Dodaj nowy element**, przejdź do **elementy Visual C#**  > **rozszerzalności** i wybierz **okna narzędzi niestandardowych**. W **nazwa** pola w dolnej części okna dialogowego, Zmień nazwę pliku, aby `ProjectPropertiesToolWindow.cs`. Aby uzyskać więcej informacji o sposobie tworzenia niestandardowego okna narzędzi, zobacz [Tworzenie rozszerzenia za pomocą okna narzędzia](../extensibility/creating-an-extension-with-a-tool-window.md).

3. Skompiluj rozwiązanie, a następnie sprawdź, czy kompiluje bez błędów.

### <a name="to-display-project-properties-in-a-tool-window"></a>Aby wyświetlić właściwości projektu w oknie narzędzi

1. W pliku ProjectPropertiesToolWindowCommand.cs, Dodaj następujące instrukcje using.

    ```csharp
    using EnvDTE;
    using System.Windows.Controls;

    ```

2. W *ProjectPropertiesToolWindowControl.xaml*, Usuń istniejące przycisku i Dodaj TreeView z przybornika. Można również usunąć program obsługi zdarzeń kliknięcie z *ProjectPropertiesToolWindowControl.xaml.cs* pliku.

3. W *ProjectPropertiesToolWindowCommand.cs*, użyj `ShowToolWindow()` metodę do otwarcia projektu i jego właściwości odczytu następnie dodać właściwości do widoku drzewa. Kod ShowToolWindow powinien wyglądać następująco:

    ```csharp
    private void ShowToolWindow(object sender, EventArgs e)
    {
        ToolWindowPane window = this.package.FindToolWindow(typeof(ProjectPropertiesToolWindow), 0, true);
        if ((null == window) || (null == window.Frame))
        {
            throw new NotSupportedException("Cannot create window.");
        }
        IVsWindowFrame windowFrame = (IVsWindowFrame)window.Frame;
        Microsoft.VisualStudio.ErrorHandler.ThrowOnFailure(windowFrame.Show());

        // Get the tree view and populate it if there is a project open.
        ProjectPropertiesToolWindowControl control = (ProjectPropertiesToolWindowControl)window.Content;
        TreeView treeView = control.treeView;

        // Reset the TreeView to 0 items.
        treeView.Items.Clear();

        DTE dte = (DTE)this.ServiceProvider.GetService(typeof(DTE));
        Projects projects = dte.Solution.Projects;
        if (projects.Count == 0)   // no project is open
        {
            TreeViewItem item = new TreeViewItem();
            item.Name = "Projects";
            item.ItemsSource = new string[]{ "no projects are open." };
            item.IsExpanded = true;
            treeView.Items.Add(item);
            return;
        }

        Project project = projects.Item(1);
        TreeViewItem item1 = new TreeViewItem();
        item1.Header = project.Name + "Properties";
        treeView.Items.Add(item1);

        foreach (Property property in project.Properties)
        {
            TreeViewItem item = new TreeViewItem();
            item.ItemsSource = new string[] { property.Name };
            item.IsExpanded = true;
            treeView.Items.Add(item);
        }
    }
    ```

4. Skompiluj projekt, a następnie rozpocząć debugowanie. Wystąpienie eksperymentalne powinna zostać wyświetlona.

5. W doświadczalnym wystąpieniu Otwórz projekt.

6. W **widoku** > **Windows inne** kliknij **ProjectPropertiesToolWindow**.

  Kontrolka drzewa w oknie narzędzia wraz z nazwą pierwszego projektu i jego właściwości projektu powinien zostać wyświetlony.