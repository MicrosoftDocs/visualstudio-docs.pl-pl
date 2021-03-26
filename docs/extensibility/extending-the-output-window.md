---
title: Rozszerzanie Okno Dane wyjściowe | Microsoft Docs
description: Dowiedz się, jak rozłożyć okno danych wyjściowych w zestawie SDK programu Visual Studio oraz utworzyć własne okienka niestandardowe i zarządzać nimi.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Output window, about Output window
ms.assetid: b02fa88c-f92a-4ff6-ba5f-2eb4d48a643a
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: cf875d070d27d307380f23e71af2bda7c4a205b5
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/25/2021
ms.locfileid: "105075045"
---
# <a name="extend-the-output-window"></a>Rozwiń okno danych wyjściowych
Okno **dane wyjściowe** to zestaw okienek tekstu do odczytu i zapisu. Program Visual Studio zawiera następujące wbudowane okienka: **kompilacja**, w której projekty komunikują się z komunikatami o kompilacjach, a **Ogólne**, w którym [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] KOMUNIKUJĄ się komunikaty dotyczące środowiska IDE. Projekty uzyskują odwołanie do okienka **kompilacji** automatycznie za pośrednictwem <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildableProjectCfg> metod interfejsu, a program Visual Studio oferuje bezpośredni dostęp do okienka **Ogólne** za pośrednictwem <xref:Microsoft.VisualStudio.Shell.Interop.SVsGeneralOutputWindowPane> usługi. Oprócz wbudowanych okienek można tworzyć własne okienka niestandardowe i zarządzać nimi.

 Okno **dane wyjściowe** można kontrolować bezpośrednio za pomocą <xref:Microsoft.VisualStudio.Shell.Interop.IVsOutputWindow> interfejsów i <xref:Microsoft.VisualStudio.Shell.Interop.IVsOutputWindowPane> . <xref:Microsoft.VisualStudio.Shell.Interop.IVsOutputWindow>Interfejs, który jest oferowany przez <xref:Microsoft.VisualStudio.Shell.Interop.SVsOutputWindow> usługę, definiuje metody tworzenia, pobierania i niszczenia okien **wyjściowych** . <xref:Microsoft.VisualStudio.Shell.Interop.IVsOutputWindowPane>Interfejs definiuje metody wyświetlania okienek, ukrywania okienek i manipulowania tekstem. Alternatywny sposób kontrolowania okna **danych wyjściowych** odbywa się za <xref:EnvDTE.OutputWindow> pomocą <xref:EnvDTE.OutputWindowPane> obiektów i w modelu obiektów automatyzacji programu Visual Studio. Te obiekty hermetyzują niemal wszystkie funkcje <xref:Microsoft.VisualStudio.Shell.Interop.IVsOutputWindow> <xref:Microsoft.VisualStudio.Shell.Interop.IVsOutputWindowPane> interfejsów i. Ponadto <xref:EnvDTE.OutputWindow> <xref:EnvDTE.OutputWindowPane> obiekty i dodają niektóre funkcje wyższego poziomu, aby ułatwić wyliczanie okien **wyjściowych** i pobieranie tekstu z okienek.

## <a name="create-an-extension-that-uses-the-output-pane"></a>Tworzenie rozszerzenia korzystającego z okienka danych wyjściowych
 Można utworzyć rozszerzenie, które wykonuje różne aspekty okienka danych wyjściowych.

1. Utwórz projekt VSIX o nazwie `TestOutput` przy użyciu polecenia menu o nazwie **TestOutput**. Aby uzyskać więcej informacji, zobacz [Tworzenie rozszerzenia za pomocą polecenia menu](../extensibility/creating-an-extension-with-a-menu-command.md).

2. Dodaj następujące odwołania:

    1. EnvDTE

    2. EnvDTE80

3. W *TestOutput. cs* Dodaj następującą instrukcję using:

    ```f#
    using EnvDTE;
    using EnvDTE80;
    ```

4. W *TestOutput. cs* Usuń `ShowMessageBox` metodę. Dodaj następujący skrót metody:

    ```csharp
    private void OutputCommandHandler(object sender, EventArgs e)
    {
    }
    ```

5. W konstruktorze TestOutput Zmień procedurę obsługi poleceń na OutputCommandHandler. Oto część, która dodaje polecenia:

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

6. W poniższych sekcjach znajdują się różne metody, które pokazują różne sposoby postępowania w okienku danych wyjściowych. Można wywołać te metody do treści `OutputCommandHandler()` metody. Na przykład poniższy kod dodaje `CreatePane()` metodę podaną w następnej sekcji.

    ```csharp
    private void OutputCommandHandler(object sender, EventArgs e)
    {
        CreatePane(new Guid(), "Created Pane", true, false);
    }
    ```

## <a name="create-an-output-window-with-ivsoutputwindow"></a>Utwórz okno danych wyjściowych za pomocą IVsOutputWindow
 Ten przykład pokazuje, jak utworzyć nowe okienko okna **danych wyjściowych** za pomocą <xref:Microsoft.VisualStudio.Shell.Interop.IVsOutputWindow> interfejsu.

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

 Jeśli ta metoda zostanie dodana do rozszerzenia podanego w poprzedniej sekcji, po kliknięciu polecenia **Invoke TestOutput** powinno zostać wyświetlone okno **dane wyjściowe** z nagłówkiem, który **wyświetla dane wyjściowe z: CreatedPane** i słowa **to zostało utworzone** w okienku.

## <a name="create-an-output-window-with-outputwindow"></a>Utwórz okno danych wyjściowych za pomocą OutputWindow
 Ten przykład przedstawia sposób tworzenia okienka okna **danych wyjściowych** przy użyciu <xref:EnvDTE.OutputWindow> obiektu.

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

 Mimo że <xref:EnvDTE.OutputWindowPanes> Kolekcja umożliwia pobieranie okienka **danych wyjściowych** według jego tytułu, tytuły okienka nie są gwarantowane jako unikatowe. Gdy nie masz wątpliwości co do unikalności tytułu, użyj <xref:Microsoft.VisualStudio.Shell.Interop.IVsOutputWindow.GetPane%2A> metody, aby pobrać odpowiednie okienko według identyfikatora GUID.

 Jeśli ta metoda zostanie dodana do rozszerzenia podanego w poprzedniej sekcji, po kliknięciu polecenia **Invoke TestOutput** powinno zostać wyświetlone okno dane wyjściowe z nagłówkiem, który **wyświetla dane wyjściowe z: DTEPane** , a w okienku **Dodano** nowe wyrazy w okienku.

## <a name="delete-an-output-window"></a>Usuń okno danych wyjściowych
 Ten przykład pokazuje, jak usunąć okienko okna **danych wyjściowych** .

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

 Jeśli ta metoda zostanie dodana do rozszerzenia podanego w poprzedniej sekcji, po kliknięciu polecenia **Invoke TestOutput** powinno zostać wyświetlone okno danych wyjściowych z nagłówkiem zawierającym wartość **Pokaż dane wyjściowe z: nowe okienko** i słowa **dodane utworzone** w okienku. Jeśli klikniesz polecenie **Wywołaj TestOutput** ponownie, okienko zostanie usunięte.

## <a name="get-the-general-pane-of-the-output-window"></a>Pobierz okienko Ogólne okna danych wyjściowych
 Ten przykład pokazuje, jak uzyskać wbudowane okienko **Ogólne** okna **dane wyjściowe** .

```csharp
IVsOutputWindowPane GetGeneralPane()
{
    return (IVsOutputWindowPane)GetService(
        typeof(SVsGeneralOutputWindowPane));
}
```

 Jeśli ta metoda zostanie dodana do rozszerzenia podanego w poprzedniej sekcji, po kliknięciu polecenia **Invoke TestOutput** powinna zostać wyświetlona informacja, że w oknie **danych wyjściowych** znajdują się wyrazy Znalezione w okienku **Ogólne** w okienku.

## <a name="get-the-build-pane-of-the-output-window"></a>Pobierz okienko kompilacji w oknie danych wyjściowych
 Ten przykład pokazuje, jak znaleźć okienko **kompilacja** i zapisać w nim. Ponieważ okienko **kompilacja** nie jest domyślnie aktywowane, uaktywnia je również.

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
