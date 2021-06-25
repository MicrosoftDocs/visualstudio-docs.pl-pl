---
title: Rozszerzanie Okno Dane wyjściowe | Microsoft Docs
description: Dowiedz się, jak rozszerzyć okno Dane wyjściowe w Visual Studio SDK oraz jak tworzyć własne okienka niestandardowe i zarządzać nimi.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- Output window, about Output window
ms.assetid: b02fa88c-f92a-4ff6-ba5f-2eb4d48a643a
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 402c53691525530171edafd6a0751dfc72c9798d
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/25/2021
ms.locfileid: "112900231"
---
# <a name="extend-the-output-window"></a>Rozszerzanie okna Dane wyjściowe
Okno **Dane** wyjściowe to zestaw okienek tekstowych do odczytu/zapisu. Visual Studio wbudowane okienka: kompilacja , w której projekty komunikują komunikaty o kompilacjach, i Ogólne **,** w których komunikuje komunikaty dotyczące [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] środowiska IDE. Projekty automatycznie pobierają odwołanie do okienka Kompilacja za pośrednictwem metod interfejsu, a program Visual Studio bezpośredni dostęp do okienka  <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildableProjectCfg> **Ogólne** za pośrednictwem <xref:Microsoft.VisualStudio.Shell.Interop.SVsGeneralOutputWindowPane> usługi. Oprócz wbudowanych okienek można tworzyć własne okienka niestandardowe i zarządzać nimi.

 Okno Dane wyjściowe można **kontrolować** bezpośrednio za pomocą <xref:Microsoft.VisualStudio.Shell.Interop.IVsOutputWindow> <xref:Microsoft.VisualStudio.Shell.Interop.IVsOutputWindowPane> interfejsów i . Interfejs, który jest oferowany przez usługę, definiuje metody tworzenia, pobierania i niszczenia okienek <xref:Microsoft.VisualStudio.Shell.Interop.IVsOutputWindow> <xref:Microsoft.VisualStudio.Shell.Interop.SVsOutputWindow> okienek danych wyjściowych.  Interfejs <xref:Microsoft.VisualStudio.Shell.Interop.IVsOutputWindowPane> definiuje metody wyświetlania okienek, ukrywania okienek i manipulowania ich tekstem. Alternatywnym sposobem kontrolowania okna **Dane** wyjściowe jest za pośrednictwem obiektów <xref:EnvDTE.OutputWindow> i w modelu obiektów Visual Studio <xref:EnvDTE.OutputWindowPane> Automation. Te obiekty hermetyzują niemal wszystkie funkcje <xref:Microsoft.VisualStudio.Shell.Interop.IVsOutputWindow> <xref:Microsoft.VisualStudio.Shell.Interop.IVsOutputWindowPane> interfejsów i . Ponadto obiekty i dodają pewne funkcje wyższego poziomu, aby ułatwić wyliczanie okienek danych wyjściowych i pobieranie tekstu <xref:EnvDTE.OutputWindow> <xref:EnvDTE.OutputWindowPane> z okienek. 

## <a name="create-an-extension-that-uses-the-output-pane"></a>Tworzenie rozszerzenia, które używa okienka Dane wyjściowe
 Możesz utworzyć rozszerzenie, które wykonuje różne aspekty okienka Dane wyjściowe.

1. Utwórz projekt VSIX o nazwie `TestOutput` za pomocą polecenia menu o nazwie **TestOutput**. Aby uzyskać więcej informacji, zobacz Create an extension with a menu command (Tworzenie [rozszerzenia za pomocą polecenia menu).](../extensibility/creating-an-extension-with-a-menu-command.md)

2. Dodaj następujące odwołania:

    1. Envdte

    2. EnvDTE80

3. W *instrukcje TestOutput.cs* dodaj następującą instrukcje using:

    ```f#
    using EnvDTE;
    using EnvDTE80;
    ```

4. W *plikach TestOutput.cs* usuń `ShowMessageBox` metodę . Dodaj następujący wycinki metody:

    ```csharp
    private void OutputCommandHandler(object sender, EventArgs e)
    {
    }
    ```

5. W konstruktorze TestOutput zmień program obsługi poleceń na OutputCommandHandler. Oto część, która dodaje polecenia:

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

6. Poniższe sekcje mają różne metody, które pokazują różne sposoby radzenia sobie z okienkiem Dane wyjściowe. Te metody można wywołać do treści `OutputCommandHandler()` metody. Na przykład poniższy kod dodaje metodę `CreatePane()` podaną w następnej sekcji.

    ```csharp
    private void OutputCommandHandler(object sender, EventArgs e)
    {
        CreatePane(new Guid(), "Created Pane", true, false);
    }
    ```

## <a name="create-an-output-window-with-ivsoutputwindow"></a>Tworzenie okna danych wyjściowych przy użyciu polecenia IVsOutputWindow
 W tym przykładzie pokazano, jak utworzyć nowe okienko **danych** wyjściowych przy użyciu <xref:Microsoft.VisualStudio.Shell.Interop.IVsOutputWindow> interfejsu .

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

 Jeśli dodasz tę metodę do rozszerzenia podanego w poprzedniej sekcji, po kliknięciu  polecenia Invoke **TestOutput** powinno zostać otwarte okno Dane  wyjściowe z nagłówkiem Pokaż dane wyjściowe **z: CreatedPane** i wyrazami To jest utworzone okienko w samym okienku.

## <a name="create-an-output-window-with-outputwindow"></a>Tworzenie okna danych wyjściowych za pomocą okna OutputWindow
 W tym przykładzie pokazano, jak utworzyć **okienko danych** wyjściowych przy użyciu <xref:EnvDTE.OutputWindow> obiektu .

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

 Mimo że <xref:EnvDTE.OutputWindowPanes> kolekcja umożliwia pobranie okienka **Dane** wyjściowe według tytułu, tytuły okienek nie muszą być unikatowe. W razie wątpliwości co do unikatowości tytułu użyj metody , aby pobrać poprawne <xref:Microsoft.VisualStudio.Shell.Interop.IVsOutputWindow.GetPane%2A> okienko przy użyciu jego identyfikatora GUID.

 Jeśli dodasz tę metodę do rozszerzenia podanego w poprzedniej sekcji, po kliknięciu polecenia Invoke **TestOutput** powinno zostać otwarte okno Dane wyjściowe z nagłówkiem Pokaż dane wyjściowe **z: DTEPane** i słowami Dodano okienko **DTE** w samym okienku.

## <a name="delete-an-output-window"></a>Usuwanie okna danych wyjściowych
 W tym przykładzie pokazano, jak usunąć **okienko okna** Dane wyjściowe.

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

 Jeśli dodasz tę metodę do rozszerzenia podanego w poprzedniej sekcji, po kliknięciu polecenia Invoke **TestOutput** powinno zostać otwarte okno  Dane wyjściowe z nagłówkiem Pokaż dane wyjściowe **z:** Nowe okienko i wyrazami Dodano utworzone okienko w samym okienku. Jeśli ponownie klikniesz **polecenie Wywołaj testOutput,** okienko zostanie usunięte.

## <a name="get-the-general-pane-of-the-output-window"></a>Uzyskiwanie okienka Ogólne w oknie Dane wyjściowe
 W tym przykładzie pokazano, jak uzyskać **wbudowane** okienko Ogólne w **oknie Dane** wyjściowe.

```csharp
IVsOutputWindowPane GetGeneralPane()
{
    return (IVsOutputWindowPane)GetService(
        typeof(SVsGeneralOutputWindowPane));
}
```

 Jeśli dodasz tę metodę do rozszerzenia podanego w poprzedniej sekcji, po kliknięciu polecenia Invoke TestOutput (Wywołaj **testOutput)** w oknie **Output** (Dane wyjściowe) w okienku powinny zostać wyświetlony wyrazy Found **General (Znaleziono** ogólne).

## <a name="get-the-build-pane-of-the-output-window"></a>Uzyskiwanie okienka Kompilacja w oknie Dane wyjściowe
 W tym przykładzie pokazano, jak znaleźć okienko **Kompilacja** i zapisać w nim dane. Ponieważ **okienko Kompilacja** nie jest domyślnie aktywowane, aktywuje je również.

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
