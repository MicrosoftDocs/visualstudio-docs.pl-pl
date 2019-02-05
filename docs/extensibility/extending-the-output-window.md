---
title: Rozszerzanie okna danych wyjściowych | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Output window, about Output window
ms.assetid: b02fa88c-f92a-4ff6-ba5f-2eb4d48a643a
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 10acf356ccfc790f9dd6a185c12a6ec5c26cccd3
ms.sourcegitcommit: 0342f99120fbd603b8f06f7e9166c39f2896827a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/05/2019
ms.locfileid: "55742482"
---
# <a name="extend-the-output-window"></a>Rozszerzanie okna danych wyjściowych
**Dane wyjściowe** okno to zbiór okienek tekstu odczytu/zapisu. Program Visual Studio zawiera te okienka wbudowane: **Tworzenie**, w projektach, które komunikują się komunikaty dotyczące kompilacji i **ogólne**, w którym [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] komunikuje się komunikaty dotyczące środowiska IDE. Projekty odwołać się do **kompilacji** automatycznie za pomocą okienka <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildableProjectCfg> metody interfejsu i programu Visual Studio zapewnia bezpośredni dostęp do **ogólne** okienko za pośrednictwem <xref:Microsoft.VisualStudio.Shell.Interop.SVsGeneralOutputWindowPane> Usługa. Oprócz wbudowanych okienek można tworzyć i zarządzać własnych niestandardowych okienek.  
  
 Możesz kontrolować **dane wyjściowe** bezpośrednio za pomocą okna <xref:Microsoft.VisualStudio.Shell.Interop.IVsOutputWindow> i <xref:Microsoft.VisualStudio.Shell.Interop.IVsOutputWindowPane> interfejsów. <xref:Microsoft.VisualStudio.Shell.Interop.IVsOutputWindow> Interfejs, który jest oferowany przez <xref:Microsoft.VisualStudio.Shell.Interop.SVsOutputWindow> usługi, definiuje metody do tworzenia, pobierania i niszczenie **dane wyjściowe** okienka. <xref:Microsoft.VisualStudio.Shell.Interop.IVsOutputWindowPane> Interfejs definiuje metody wyświetlanie okienek, ukrywanie okienka i manipulowania ich tekst. Alternatywny sposób kontrolowania **dane wyjściowe** okno jest za pośrednictwem <xref:EnvDTE.OutputWindow> i <xref:EnvDTE.OutputWindowPane> obiekty w modelu obiektów automatyzacji usługi Visual Studio. Te obiekty hermetyzują prawie wszystkie funkcje <xref:Microsoft.VisualStudio.Shell.Interop.IVsOutputWindow> i <xref:Microsoft.VisualStudio.Shell.Interop.IVsOutputWindowPane> interfejsów. Ponadto <xref:EnvDTE.OutputWindow> i <xref:EnvDTE.OutputWindowPane> obiektów dodać niektóre funkcje wyższego poziomu, aby ułatwić wyliczyć **dane wyjściowe** okienka i pobrać tekst z okienka.  
  
## <a name="create-an-extension-that-uses-the-output-pane"></a>Tworzenie rozszerzenia, które używa okienko danych wyjściowych  
 Istnieje możliwość rozszerzenia, które wykonuje różne aspekty okienko danych wyjściowych.  
  
1.  Utwórz projekt VSIX, o nazwie `TestOutput` za pomocą polecenia menu o nazwie **TestOutput**. Aby uzyskać więcej informacji, zobacz [Tworzenie rozszerzenia za pomocą polecenia menu](../extensibility/creating-an-extension-with-a-menu-command.md).  
  
2.  Dodaj następujące odwołania:  
  
    1.  EnvDTE  
  
    2.  EnvDTE80  
  
3.  W *TestOutput.cs*, dodaj następującą instrukcję using:  
  
    ```f#  
    using EnvDTE;  
    using EnvDTE80;  
    ```  
  
4.  W *TestOutput.cs*, Usuń `ShowMessageBox` metody. Dodaj następujące szkieletu metody:  
  
    ```csharp  
    private void OutputCommandHandler(object sender, EventArgs e)  
    {  
    }  
    ```  
  
5.  W Konstruktorze TestOutput zmienić program obsługi poleceń do OutputCommandHandler. Oto części, które umożliwia dodanie polecenia:  
  
    ```csharp  
    OleMenuCommandService commandService = this.ServiceProvider.GetService(typeof(IMenuCommandService)) as OleMenuCommandService;  
    if (commandService != null)  
    {  
        CommandID menuCommandID = new CommandID(MenuGroup, CommandId);  
        EventHandler eventHandler = OutputCommandHandler;  
        MenuCommand menuItem = new MenuCommand(eventHandler, menuCommandID);  
        commandService.AddCommand(menuItem);  
    }  
    ```  
  
6.  Poniższe sekcje mają różne metody, które pokazują różne sposoby radzenia sobie z okienkiem danych wyjściowych. Może wywoływać te metody, aby treść `OutputCommandHandler()` metody. Na przykład, poniższy kod dodaje `CreatePane()` metody podanej w następnej sekcji.  
  
    ```csharp  
    private void OutputCommandHandler(object sender, EventArgs e)  
    {  
        CreatePane(new Guid(), "Created Pane", true, false);  
    }  
    ```  
  
## <a name="create-an-output-window-with-ivsoutputwindow"></a>Utwórz okno danych wyjściowych z IVsOutputWindow  
 Ten przykład pokazuje, jak utworzyć nową **dane wyjściowe** okienko przy użyciu <xref:Microsoft.VisualStudio.Shell.Interop.IVsOutputWindow> interfejsu.  
  
```csharp  
void CreatePane(Guid paneGuid, string title,   
    bool visible, bool clearWithSolution)  
{  
    IVsOutputWindow output =   
        (IVsOutputWindow)GetService(typeof(SVsOutputWindow));  
    IVsOutputWindowPane pane;  
  
    // Create a new pane.  
    output.CreatePane(  
        ref paneGuid,   
        title,   
        Convert.ToInt32(visible),   
        Convert.ToInt32(clearWithSolution));  
  
    // Retrieve the new pane.  
    output.GetPane(ref paneGuid, out pane);  
  
     pane.OutputString("This is the Created Pane \n");  
}  
```  
  
 Jeśli dodasz tę metodę rozszerzenia, podany w poprzedniej sekcji, po kliknięciu **wywołania TestOutput** polecenia powinien zostać wyświetlony **dane wyjściowe** okna z nagłówkiem, który jest wyświetlany komunikat **Pokaż dane wyjściowe od: CreatedPane** i wyrazy **to okienko utworzone** w okienku sam.  
  
## <a name="create-an-output-window-with-outputwindow"></a>Utwórz okno danych wyjściowych z outputwindow —  
 W tym przykładzie przedstawiono sposób tworzenia **dane wyjściowe** okienko przy użyciu <xref:EnvDTE.OutputWindow> obiektu.  
  
```csharp  
void CreatePane(string title)  
{  
    DTE2 dte = (DTE2)GetService(typeof(DTE));  
    OutputWindowPanes panes =  
        dte.ToolWindows.OutputWindow.OutputWindowPanes;  
  
    try  
    {  
        // If the pane exists already, write to it.  
        panes.Item(title);  
    }  
    catch (ArgumentException)  
    {  
        // Create a new pane and write to it.  
        panes.Add(title);  
    }  
}  
```  
  
 Mimo że <xref:EnvDTE.OutputWindowPanes> kolekcji umożliwia pobranie **dane wyjściowe** okienko przez jego tytuł, okienko tytuły są nie musi być unikatowy. Jeśli unikatowości tytuł jest wątpliwości, użyj <xref:Microsoft.VisualStudio.Shell.Interop.IVsOutputWindow.GetPane%2A> metodę, aby pobrać poprawną okienko przez jego identyfikator GUID.  
  
 Jeśli dodasz tę metodę rozszerzenia, podany w poprzedniej sekcji, po kliknięciu **wywołania TestOutput** polecenia powinien zostać wyświetlony w oknie danych wyjściowych z nagłówkiem, który jest wyświetlany komunikat **Pokaż dane wyjściowe: DTEPane** i wyrazy **dodano okienko DTE** w okienku sam.  
  
## <a name="delete-an-output-window"></a>Usuń okno danych wyjściowych  
 W tym przykładzie przedstawiono sposób usuwania **dane wyjściowe** okienko.  
  
```csharp  
void DeletePane(Guid paneGuid)  
{  
    IVsOutputWindow output =  
    (IVsOutputWindow)ServiceProvider.GetService(typeof(SVsOutputWindow));  
  
    IVsOutputWindowPane pane;  
    output.GetPane(ref paneGuid, out pane);  
  
    if (pane == null)  
    {  
        CreatePane(paneGuid, "New Pane\n", true, true);  
    }  
     else  
    {  
        output.DeletePane(ref paneGuid);  
    }  
}  
```  
  
 Jeśli dodasz tę metodę rozszerzenia, podany w poprzedniej sekcji, po kliknięciu **wywołania TestOutput** polecenia powinien zostać wyświetlony w oknie danych wyjściowych z nagłówkiem, który jest wyświetlany komunikat **Pokaż dane wyjściowe: Nowe okienko** i wyrazy **dodano okienko utworzone** w okienku sam. Jeśli klikniesz **wywołania TestOutput** polecenie ponownie, okienko zostanie usunięty.  
  
## <a name="get-the-general-pane-of-the-output-window"></a>Pobierz ogólne okienka w oknie danych wyjściowych  
 W tym przykładzie pokazano, jak uzyskać wbudowane **ogólne** okienku **dane wyjściowe** okna.  
  
```csharp  
void GetGeneralPane()  
{  
    return (IVsOutputWindowPane)GetService(  
        typeof(SVsGeneralOutputWindowPane));  
}  
```  
  
 Jeśli dodasz tę metodę rozszerzenia, podany w poprzedniej sekcji, po kliknięciu **wywołania TestOutput** polecenia powinien zostać wyświetlony, który **dane wyjściowe** okno zawiera wyrazy **znaleźć ogólne w okienku** w okienku.  
  
## <a name="get-the-build-pane-of-the-output-window"></a>Pobierz okienka kompilacji w oknie danych wyjściowych  
 W tym przykładzie pokazano, jak znaleźć **kompilacji** okienka i zapis do niego. Ponieważ **kompilacji** okienko nie jest aktywowana domyślnie, zostaje uaktywniony również.  
  
```csharp  
void OutputTaskItemStringExExample(string buildMessage)  
{  
    EnvDTE80.DTE2 dte = (EnvDTE80.DTE2)ServiceProvider.GetService(typeof(EnvDTE.DTE));  
  
    EnvDTE.OutputWindowPanes panes =  
        dte.ToolWindows.OutputWindow.OutputWindowPanes;  
    foreach (EnvDTE.OutputWindowPane pane in panes)  
        {  
            if (pane.Name.Contains("Build"))  
            {  
                pane.OutputString(buildMessage + "\n");  
                pane.Activate();  
                return;  
             }  
        }  
}  
```
