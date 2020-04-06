---
title: Uzyskiwanie właściwości projektu | Dokumenty firmy Microsoft
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
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80711414"
---
# <a name="get-project-properties"></a>Uzyskaj właściwości projektu

W tym przewodniku pokazano, jak wyświetlać właściwości projektu w oknie narzędzia.

## <a name="prerequisites"></a>Wymagania wstępne

Począwszy od programu Visual Studio 2015, nie należy instalować visual studio SDK z centrum pobierania. Jest on dołączony jako opcjonalna funkcja w konfiguracji programu Visual Studio. Można również zainstalować vs SDK później. Aby uzyskać więcej informacji, zobacz [Instalowanie pakietu SDK programu Visual Studio](../extensibility/installing-the-visual-studio-sdk.md).

### <a name="to-create-a-vsix-project-and-add-a-tool-window"></a>Aby utworzyć projekt VSIX i dodać okno narzędzia

1. Każde rozszerzenie programu Visual Studio rozpoczyna się od projektu wdrożenia VSIX, który będzie zawierał zasoby rozszerzenia. Utwórz [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] projekt VSIX o nazwie `ProjectPropertiesExtension`. Szablon projektu VSIX można znaleźć w oknie dialogowym **Nowy projekt,** wyszukując "vsix".

2. Dodaj okno narzędzia, dodając szablon elementu `ProjectPropertiesToolWindow`niestandardowego okna narzędzia o nazwie . W **Eksploratorze rozwiązań**kliknij prawym przyciskiem myszy węzeł projektu i wybierz polecenie **Dodaj** > **nowy element**. W **oknie dialogowym Dodawanie nowego elementu**przejdź do pozycji**Rozszerzalność** **elementów** > programu Visual C# i wybierz pozycję **Okno narzędzia niestandardowego**. W polu **Nazwa** u dołu okna dialogowego `ProjectPropertiesToolWindow.cs`zmień nazwę pliku na . Aby uzyskać więcej informacji na temat tworzenia niestandardowego okna narzędzia, zobacz [Tworzenie rozszerzenia z oknem narzędzia](../extensibility/creating-an-extension-with-a-tool-window.md).

3. Skompiluj rozwiązanie i sprawdź, czy kompiluje się bez błędów.

### <a name="to-display-project-properties-in-a-tool-window"></a>Aby wyświetlić właściwości projektu w oknie narzędzia

1. W pliku ProjectPropertiesToolWindowCommand.cs dodaj następujące elementy za pomocą dyrektyw.

    ```csharp
    using EnvDTE;
    using System.Windows.Controls;

    ```

2. W *pliku ProjectPropertiesToolWindowControl.xaml*usuń istniejący przycisk i dodaj widok drzewa z przybornika. Można również usunąć program obsługi zdarzeń kliknięcia z pliku *ProjectPropertiesToolWindowControl.xaml.cs.*

3. W *ProjectPropertiesToolWindowCommand.cs*, użyj `ShowToolWindow()` metody, aby otworzyć projekt i odczytać jego właściwości, a następnie dodać właściwości do TreeView. Kod dla ShowToolWindow powinien wyglądać następująco:

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

4. Skompiluj projekt i rozpocznij debugowanie. Powinno pojawić się wystąpienie eksperymentalne.

5. W wystąpieniu eksperymentalnym otwórz projekt.

6. W **widoku** > **innego systemu Windows** kliknij pozycję **ProjectPropertiesToolWindow**.

  Formant drzewa powinien zostać wyświetlony w oknie narzędzia wraz z nazwą pierwszego projektu i wszystkich jego właściwości projektu.
