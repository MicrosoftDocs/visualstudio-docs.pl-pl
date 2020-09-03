---
title: Pobieranie właściwości projektu | Microsoft Docs
ms.date: 3/16/2019
ms.topic: conceptual
helpviewer_keywords:
- project properties, displaying in tool window
- tool windows, displaying project properties
ms.assetid: 96ba07ca-0811-4013-8602-12550ac4ba79
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 9ddfd48827bc762c9189f9b7600cfe9200e5c866
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "80711414"
---
# <a name="get-project-properties"></a>Pobierz właściwości projektu

W tym instruktażu pokazano, jak wyświetlić właściwości projektu w oknie narzędzi.

## <a name="prerequisites"></a>Wymagania wstępne

Począwszy od programu Visual Studio 2015, nie należy instalować zestawu Visual Studio SDK z centrum pobierania. Jest ona dostępna jako opcjonalna funkcja w Instalatorze programu Visual Studio. Zestaw VS SDK można także zainstalować później. Aby uzyskać więcej informacji, zobacz [Instalowanie zestawu Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).

### <a name="to-create-a-vsix-project-and-add-a-tool-window"></a>Aby utworzyć projekt VSIX i dodać okno narzędzi

1. Każde rozszerzenie programu Visual Studio rozpoczyna się od projektu wdrożenia VSIX, który będzie zawierać zasoby rozszerzenia. Utwórz [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Projekt VSIX o nazwie `ProjectPropertiesExtension` . Szablon projektu VSIX można znaleźć w oknie dialogowym **Nowy projekt** , wyszukując frazę "VSIX".

2. Dodaj okno narzędzi, dodając szablon elementu niestandardowego okna narzędzi o nazwie `ProjectPropertiesToolWindow` . W **Eksplorator rozwiązań**kliknij prawym przyciskiem myszy węzeł projektu i wybierz polecenie **Dodaj**  >  **nowy element**. W **oknie dialogowym Dodaj nowy element**przejdź do obszaru rozszerzanie **elementów Visual C#**  >  **Extensibility** i wybierz **niestandardowe okno narzędzi**. W polu **Nazwa** w dolnej części okna dialogowego Zmień nazwę pliku na `ProjectPropertiesToolWindow.cs` . Aby uzyskać więcej informacji na temat tworzenia niestandardowego okna narzędzi, zobacz [Tworzenie rozszerzenia przy użyciu okna narzędzi](../extensibility/creating-an-extension-with-a-tool-window.md).

3. Skompiluj rozwiązanie i sprawdź, czy jest ono kompilowane bez błędów.

### <a name="to-display-project-properties-in-a-tool-window"></a>Aby wyświetlić właściwości projektu w oknie narzędzi

1. W pliku ProjectPropertiesToolWindowCommand.cs Dodaj następujące dyrektywy using.

    ```csharp
    using EnvDTE;
    using System.Windows.Controls;

    ```

2. W *ProjectPropertiesToolWindowControl. XAML*usuń istniejący przycisk i Dodaj element TreeView z przybornika. Możesz również usunąć procedurę obsługi zdarzeń kliknięcia z pliku *ProjectPropertiesToolWindowControl.XAML.cs* .

3. W *ProjectPropertiesToolWindowCommand.cs*Użyj metody, `ShowToolWindow()` Aby otworzyć projekt i odczytać jego właściwości, a następnie Dodaj właściwości do widoku TreeView. Kod dla ShowToolWindow powinien wyglądać następująco:

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

4. Skompiluj projekt i Rozpocznij debugowanie. Powinno zostać wyświetlone wystąpienie eksperymentalne.

5. W eksperymentalnym wystąpieniu Otwórz projekt.

6. W **widoku**  >  **inne okna** kliknij **ProjectPropertiesToolWindow**.

  Kontrolka drzewa powinna zostać wyświetlona w oknie narzędzia wraz z nazwą pierwszego projektu i wszystkimi jego właściwościami projektu.
