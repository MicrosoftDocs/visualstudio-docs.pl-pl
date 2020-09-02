---
title: Pobieranie właściwości projektu | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- project properties, displaying in tool window
- tool windows, displaying project properties
ms.assetid: 96ba07ca-0811-4013-8602-12550ac4ba79
caps.latest.revision: 30
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: d0557d08c318eda47853ec69c6204739cbece560
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "68204323"
---
# <a name="getting-project-properties"></a>Pobieranie właściwości projektu
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

W tym instruktażu pokazano, jak wyświetlić właściwości projektu w oknie narzędzi.  
  
## <a name="prerequisites"></a>Wymagania wstępne  
 Począwszy od programu Visual Studio 2015, nie należy instalować zestawu Visual Studio SDK z centrum pobierania. Jest ona dostępna jako opcjonalna funkcja w Instalatorze programu Visual Studio. Zestaw VS SDK można także zainstalować później. Aby uzyskać więcej informacji, zobacz [Instalowanie zestawu Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).  
  
### <a name="to-create-a-vsix-project-and-add-a-tool-window"></a>Aby utworzyć projekt VSIX i dodać okno narzędzi  
  
1. Każde rozszerzenie programu Visual Studio rozpoczyna się od projektu wdrożenia VSIX, który będzie zawierać zasoby rozszerzenia. Utwórz [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] Projekt VSIX o nazwie `ProjectPropertiesExtension` . Szablon projektu VSIX można znaleźć w oknie dialogowym **Nowy projekt** w obszarze **Visual C#/rozszerzalność**.  
  
2. Dodaj okno narzędzi, dodając szablon elementu niestandardowego okna narzędzi o nazwie `ProjectPropertiesToolWindow` . W **Eksplorator rozwiązań**kliknij prawym przyciskiem myszy węzeł projektu i wybierz polecenie **Dodaj/nowy element**. W **oknie dialogowym Dodaj nowy element**przejdź do **pozycji Visual C# elementy/rozszerzalność** i wybierz **niestandardowe okno narzędzi**. W polu **Nazwa** w dolnej części okna dialogowego Zmień nazwę pliku na `ProjectPropertiesToolWindow.cs` . Aby uzyskać więcej informacji na temat tworzenia niestandardowego okna narzędzi, zobacz [Tworzenie rozszerzenia przy użyciu okna narzędzi](../extensibility/creating-an-extension-with-a-tool-window.md).  
  
3. Skompiluj rozwiązanie i sprawdź, czy jest ono kompilowane bez błędów.  
  
### <a name="to-display-project-properties-in-a-tool-window"></a>Aby wyświetlić właściwości projektu w oknie narzędzi  
  
1. W pliku ProjectPropertiesToolWindowCommand.cs Dodaj następujące instrukcje using.  
  
    ```csharp  
    using EnvDTE;  
    using System.Windows.Controls;  
  
    ```  
  
2. W ProjectPropertiesToolWindowControl. XAML usuń istniejący przycisk i Dodaj element TreeView z przybornika. Możesz również usunąć procedurę obsługi zdarzeń kliknięcia z pliku ProjectPropertiesToolWindowControl.xaml.cs.  
  
3. W ProjectPropertiesToolWindowCommand.cs, użyj metody ShowToolWindow (), aby otworzyć projekt i odczytać jego właściwości, a następnie Dodaj właściwości do widoku drzewa. Kod dla ShowToolWindow powinien wyglądać następująco:  
  
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
  
6. W **widoku/innych oknach** kliknij **ProjectPropertiesToolWindow**.  
  
     Kontrolka drzewa powinna zostać wyświetlona w oknie narzędzia wraz z nazwą pierwszego projektu i wszystkimi jego właściwościami projektu.
