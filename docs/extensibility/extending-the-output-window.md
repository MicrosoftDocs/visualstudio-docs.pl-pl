---
title: Rozszerzanie okna wyjściowego | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Output window, about Output window
ms.assetid: b02fa88c-f92a-4ff6-ba5f-2eb4d48a643a
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 800b443b079111d1d09fffdd900b246a020578f4
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80711641"
---
# <a name="extend-the-output-window"></a>Rozszerzanie okna Wyjście
Okno **Dane wyjściowe** to zestaw okienek tekstu odczytu/zapisu. Visual Studio ma te wbudowane okienka: **Kompilacja**, w **General**którym projekty [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] komunikują wiadomości o kompilacjach i Ogólne , w którym komunikuje się wiadomości o IDE. Projekty uzyskać odwołanie do **kompilacji** okienka <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildableProjectCfg> automatycznie za pośrednictwem metod interfejsu i Visual Studio <xref:Microsoft.VisualStudio.Shell.Interop.SVsGeneralOutputWindowPane> oferuje bezpośredni dostęp do **ogólnego** okienka za pośrednictwem usługi. Oprócz wbudowanych okienek można tworzyć własne okienka niestandardowe i zarządzać nimi.

 Okno Dane **wyjściowe** można sterować bezpośrednio za pośrednictwem <xref:Microsoft.VisualStudio.Shell.Interop.IVsOutputWindow> interfejsów i <xref:Microsoft.VisualStudio.Shell.Interop.IVsOutputWindowPane> interfejsów. Interfejs, <xref:Microsoft.VisualStudio.Shell.Interop.IVsOutputWindow> który jest oferowany <xref:Microsoft.VisualStudio.Shell.Interop.SVsOutputWindow> przez usługę, definiuje metody tworzenia, pobierania i niszczenia okien **okiennych danych wyjściowych.** Interfejs <xref:Microsoft.VisualStudio.Shell.Interop.IVsOutputWindowPane> definiuje metody wyświetlania okienek, ukrywania okienek i manipulowania ich tekstem. Alternatywny sposób kontrolowania okna **dane wyjściowe** jest za pośrednictwem <xref:EnvDTE.OutputWindow> i <xref:EnvDTE.OutputWindowPane> obiektów w modelu obiektu automatyzacji programu Visual Studio. Obiekty te hermetyzują prawie wszystkie <xref:Microsoft.VisualStudio.Shell.Interop.IVsOutputWindow> funkcje <xref:Microsoft.VisualStudio.Shell.Interop.IVsOutputWindowPane> i interfejsy. Ponadto <xref:EnvDTE.OutputWindow> i <xref:EnvDTE.OutputWindowPane> obiekty dodać niektóre funkcje wyższego poziomu, aby ułatwić wyliczenie okienka okna dane **wyjściowe** i pobrać tekst z okienek.

## <a name="create-an-extension-that-uses-the-output-pane"></a>Tworzenie rozszerzenia korzystającego z okienka Dane wyjściowe
 Można wprowadzić rozszerzenie, które wykonuje różne aspekty okienka Dane wyjściowe.

1. Utwórz projekt VSIX o nazwie `TestOutput` polecenie menu o nazwie **TestOutput**. Aby uzyskać więcej informacji, zobacz [Tworzenie rozszerzenia za pomocą polecenia menu](../extensibility/creating-an-extension-with-a-menu-command.md).

2. Dodaj następujące odwołania:

    1. Envdte

    2. EnvDTE80 ( EnvDTE0 )

3. W *TestOutput.cs*dodaj następującą instrukcję za pomocą:

    ```f#
    using EnvDTE;
    using EnvDTE80;
    ```

4. W *TestOutput.cs*, usuń `ShowMessageBox` metodę. Dodaj następującą metodę skrótu:

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

6. Poniższe sekcje mają różne metody, które pokazują różne sposoby radzenia sobie z okienkiem dane wyjściowe. Można wywołać te metody `OutputCommandHandler()` do treści metody. Na przykład poniższy kod `CreatePane()` dodaje metodę podana w następnej sekcji.

    ```csharp
    private void OutputCommandHandler(object sender, EventArgs e)
    {
        CreatePane(new Guid(), "Created Pane", true, false);
    }
    ```

## <a name="create-an-output-window-with-ivsoutputwindow"></a>Tworzenie okna wyjściowego za pomocą iVsOutputWindow
 W tym przykładzie pokazano, jak utworzyć nowe <xref:Microsoft.VisualStudio.Shell.Interop.IVsOutputWindow> okienko okna **dane wyjściowe** przy użyciu interfejsu.

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

 Jeśli dodasz tę metodę do rozszerzenia podane w poprzedniej sekcji, po kliknięciu polecenia **Wywołaj TestOutput** powinien zostać wyświetlony **output** okno z nagłówkiem, który mówi **Pokaż dane wyjściowe z: CreatedPane** i słowa **To jest utworzone okienko** w samym okienku.

## <a name="create-an-output-window-with-outputwindow"></a>Tworzenie okna dane wyjściowe z outputwindow
 W tym przykładzie pokazano, jak utworzyć <xref:EnvDTE.OutputWindow> okienko okna **dane wyjściowe** przy użyciu obiektu.

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

 Mimo <xref:EnvDTE.OutputWindowPanes> że kolekcja umożliwia pobieranie okienka okna **dane wyjściowe** przez jego tytuł, tytuły okienka nie są gwarantowane, aby być unikatowe. Jeśli masz wątpliwości co do unikatowości <xref:Microsoft.VisualStudio.Shell.Interop.IVsOutputWindow.GetPane%2A> tytułu, użyj tej metody, aby pobrać odpowiednie okienko za pomocą identyfikatora GUID.

 Jeśli dodasz tę metodę do rozszerzenia podane w poprzedniej sekcji, po **kliknięciu polecenia Invoke TestOutput** powinien zostać wyświetlony output okno z nagłówkiem, który mówi **Pokaż dane wyjściowe z: DTEPane** i słowa **Dodano okienko DTE** w samym okienku.

## <a name="delete-an-output-window"></a>Usuwanie okna Dane wyjściowe
 W tym przykładzie pokazano, jak usunąć okienko okna **dane wyjściowe.**

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

 Jeśli dodasz tę metodę do rozszerzenia podane w poprzedniej sekcji, po kliknięciu polecenia **Wywołaj TestOutput** powinien zostać wyświetlony output okno z nagłówkiem, który mówi **Pokaż dane wyjściowe z: Nowe okienko** i słowa **Dodane utworzone okienko** w samym okienku. Jeśli klikniesz polecenie **Wywołaj testoutput** ponownie, okienko zostanie usunięte.

## <a name="get-the-general-pane-of-the-output-window"></a>Pobierz okienko Ogólne okna Dane wyjściowe
 W tym przykładzie pokazano, jak uzyskać wbudowane **ogólne** okienko okna **Dane wyjściowe.**

```csharp
IVsOutputWindowPane GetGeneralPane()
{
    return (IVsOutputWindowPane)GetService(
        typeof(SVsGeneralOutputWindowPane));
}
```

 Jeśli dodasz tę metodę do rozszerzenia podane w poprzedniej sekcji, po kliknięciu polecenia **Invoke TestOutput** powinien zostać wyświetlony, że okno **Dane wyjściowe** pokazuje słowa **znalezione ogólne okienka** w okienku.

## <a name="get-the-build-pane-of-the-output-window"></a>Pobierz okienko Kompilacji okna Dane wyjściowe
 W tym przykładzie pokazano, jak znaleźć **okienko kompilacji** i zapisać do niego. Ponieważ **okienko kompilacji** nie jest domyślnie aktywowane, aktywuje je również.

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
