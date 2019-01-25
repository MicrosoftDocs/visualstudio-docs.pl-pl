---
title: Pobieranie właściwości projektu | Dokumentacja firmy Microsoft
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
ms.openlocfilehash: af78a1c8e89710af73bf5f6d25cf3446cd0d50af
ms.sourcegitcommit: c496a77add807ba4a29ee6a424b44a5de89025ea
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2019
ms.locfileid: "54834368"
---
# <a name="getting-project-properties"></a>Pobieranie właściwości projektu
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Ten poradnik pokazuje jak Wyświetla właściwości projektu w oknie narzędzi.  
  
## <a name="prerequisites"></a>Wymagania wstępne  
 Począwszy od programu Visual Studio 2015, możesz nie należy instalować programu Visual Studio SDK z Centrum pobierania. Jest dołączony jako opcjonalna funkcja w Instalatorze programu Visual Studio. Możesz także zainstalować zestaw SDK programu VS później. Aby uzyskać więcej informacji, zobacz [instalowania programu Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).  
  
### <a name="to-create-a-vsix-project-and-add-a-tool-window"></a>Aby utworzyć projekt VSIX i dodać okna narzędzi  
  
1.  Każde rozszerzenie programu Visual Studio rozpoczyna się od Projekt wdrożenia VSIX, który będzie zawierać zasoby rozszerzenia. Tworzenie [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] projektu VSIX, o nazwie `ProjectPropertiesExtension`. Można znaleźć szablonu projektu VSIX w **nowy projekt** , okno dialogowe **Visual C# / rozszerzalności**.  
  
2.  Dodawanie okna narzędzi, dodając szablon elementu niestandardowego okna narzędzi o nazwie `ProjectPropertiesToolWindow`. W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy węzeł projektu i wybierz **Add / nowy element**. W **okna dialogowego Dodaj nowy element**, przejdź do **elementy Visual C# / rozszerzalności** i wybierz **okna narzędzi niestandardowych**. W **nazwa** pola w dolnej części okna dialogowego, Zmień nazwę pliku, aby `ProjectPropertiesToolWindow.cs`. Aby uzyskać więcej informacji o sposobie tworzenia niestandardowego okna narzędzi, zobacz [Tworzenie rozszerzenia za pomocą okna narzędzia](../extensibility/creating-an-extension-with-a-tool-window.md).  
  
3.  Skompiluj rozwiązanie, a następnie sprawdź, czy kompiluje bez błędów.  
  
### <a name="to-display-project-properties-in-a-tool-window"></a>Aby wyświetlić właściwości projektu w oknie narzędzi  
  
1.  W pliku ProjectPropertiesToolWindowCommand.cs Dodaj następujące instrukcje using.  
  
    ```csharp  
    using EnvDTE;  
    using System.Windows.Controls;  
  
    ```  
  
2.  W ProjectPropertiesToolWindowControl.xaml Usuń istniejące przycisk i Dodaj TreeView z przybornika. Program obsługi zdarzeń kliknięcie można również usunąć z pliku ProjectPropertiesToolWindowControl.xaml.cs.  
  
3.  W ProjectPropertiesToolWindowCommand.cs użyj metody ShowToolWindow() do otwarcia projektu i jego właściwości do odczytu, a następnie dodać właściwości do widoku drzewa. Kod ShowToolWindow powinien wyglądać następująco:  
  
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
  
4.  Skompiluj projekt, a następnie rozpocząć debugowanie. Wystąpienie eksperymentalne powinna zostać wyświetlona.  
  
5.  W doświadczalnym wystąpieniu Otwórz projekt.  
  
6.  W **widok / inne Windows** kliknij **ProjectPropertiesToolWindow**.  
  
     Kontrolka drzewa w oknie narzędzia wraz z nazwą pierwszego projektu i jego właściwości projektu powinien zostać wyświetlony.
