---
title: Pobieranie właściwości projektu | Microsoft Docs
description: Dowiedz się, jak wyświetlać właściwości projektu w oknie narzędzi. W tym przykładzie przedstawiono kontrolkę drzewa w oknie narzędzia.
ms.custom: SEO-VS-2020
ms.date: 3/16/2019
ms.topic: how-to
helpviewer_keywords:
- project properties, displaying in tool window
- tool windows, displaying project properties
ms.assetid: 96ba07ca-0811-4013-8602-12550ac4ba79
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: d3f7f6cc788e693ae143b288c589fc868c59d531
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/25/2021
ms.locfileid: "112900671"
---
# <a name="get-project-properties"></a>Uzyskiwanie właściwości projektu

W tym przewodniku pokazano, jak wyświetlać właściwości projektu w oknie narzędzi.

## <a name="prerequisites"></a>Wymagania wstępne

Począwszy od Visual Studio 2015 r., zestaw SDK usługi Visual Studio nie jest instalowany z Centrum pobierania. Jest ona dołączona jako opcjonalna funkcja w Visual Studio konfiguracji. Zestaw VS SDK można również zainstalować później. Aby uzyskać więcej informacji, zobacz [Instalowanie Visual Studio SDK.](../extensibility/installing-the-visual-studio-sdk.md)

### <a name="to-create-a-vsix-project-and-add-a-tool-window"></a>Aby utworzyć projekt VSIX i dodać okno narzędzi

1. Każde Visual Studio rozpoczyna się od projektu wdrożenia VSIX, który będzie zawierać zasoby rozszerzenia. Utwórz projekt [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] VSIX o nazwie `ProjectPropertiesExtension` . Szablon projektu VSIX można znaleźć w **oknie dialogowym Nowy projekt,** wyszukując "vsix".

2. Dodaj okno narzędzi, dodając szablon elementu niestandardowego okna narzędzi o nazwie `ProjectPropertiesToolWindow` . W **Eksplorator rozwiązań** kliknij prawym przyciskiem myszy węzeł projektu i wybierz polecenie **Dodaj**  >  **nowy element**. W **oknie dialogowym Dodawanie nowego elementu** przejdź do pozycji Rozszerzalność elementów Visual **C#**  >   i wybierz pozycję Okno **narzędzi niestandardowych.** W polu **Nazwa** w dolnej części okna dialogowego zmień nazwę pliku na `ProjectPropertiesToolWindow.cs` . Aby uzyskać więcej informacji na temat tworzenia niestandardowego okna narzędzi, zobacz [Create an extension with a tool window (Tworzenie rozszerzenia za pomocą okna narzędzi).](../extensibility/creating-an-extension-with-a-tool-window.md)

3. Skompiluj rozwiązanie i sprawdź, czy jest ono kompilowane bez błędów.

### <a name="to-display-project-properties-in-a-tool-window"></a>Aby wyświetlić właściwości projektu w oknie narzędzi

1. W pliku ProjectPropertiesToolWindowCommand.cs dodaj następujące dyrektywy using.

    ```csharp
    using EnvDTE;
    using System.Windows.Controls;

    ```

2. W *pliku ProjectPropertiesToolWindowControl.xaml* usuń istniejący przycisk i dodaj kontrolkę TreeView z przybornika. Możesz również usunąć program obsługi zdarzeń kliknięcia z *pliku ProjectPropertiesToolWindowControl.xaml.cs.*

3. W *pliku ProjectPropertiesToolWindowCommand.cs* użyj metody , aby otworzyć projekt i odczytać jego właściwości, a następnie dodaj właściwości do `ShowToolWindow()` widoku TreeView. Kod dla showToolWindow powinien wyglądać następująco:

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

4. Skompilowanie projektu i rozpoczęcie debugowania. Powinno zostać wyświetlone wystąpienie eksperymentalne.

5. W wystąpieniu eksperymentalnym otwórz projekt.

6. W widoku **Inne**  >  **okna kliknij** pozycję **ProjectPropertiesToolWindow.**

  W oknie narzędzi powinna zostać wyświetlony kontrolka drzewa wraz z nazwą pierwszego projektu i wszystkimi jego właściwościami projektu.
