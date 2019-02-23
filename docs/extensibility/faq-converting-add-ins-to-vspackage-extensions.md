---
title: 'FAQ: Konwertowanie dodatków na rozszerzenia pakietu VSPackage | Dokumentacja firmy Microsoft'
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 3a01d333-6e31-423f-ae06-5091a4fcb7a9
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 7e43c50dd006190935f8ce1eb3a17e3f268e14cd
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/22/2019
ms.locfileid: "56692830"
---
# <a name="faq-converting-add-ins-to-vspackage-extensions"></a>FAQ: Konwertowanie dodatków na rozszerzenia pakietu VSPackage
Dodatki są one przestarzałe. Aby wprowadzić nowe rozszerzenie programu Visual Studio, musisz utworzyć rozszerzenia VSIX. Poniżej przedstawiono odpowiedzi na często zadawane pytania dotyczące jak konwertować dodatek programu Visual Studio rozszerzenia VSIX.

> [!WARNING]
>  Począwszy od programu Visual Studio 2015, w przypadku projektów C# i Visual Basic można użyć projektu VSIX i dodać szablony elementów dla polecenia menu, okien narzędzi i pakiety VSPackages. Aby uzyskać więcej informacji, zobacz [What's new in Visual Studio 2015 SDK](../extensibility/what-s-new-in-the-visual-studio-2015-sdk.md).

> [!IMPORTANT]
>  W wielu przypadkach można po prostu przenieść kodu dodatku do projektu VSIX z elementem projektu pakietu VSPackage. Obiekt automatyzacji DTE można uzyskać przez wywołanie metody <xref:Microsoft.VisualStudio.Shell.Package.GetService%2A> w <xref:Microsoft.VisualStudio.Shell.Package.Initialize%2A> metody.
>
>  `DTE2 dte = (DTE2)GetService(typeof(DTE));`
>
>  Aby uzyskać więcej informacji, zobacz [jak mogę uruchomić Moje kodu dodatku w VSPackage?](../extensibility/faq-converting-add-ins-to-vspackage-extensions.md#BKMK_RunAddin) poniżej.

## <a name="what-software-do-i-need-to-develop-vsix-extensions"></a>Jakie oprogramowanie należy do tworzenia rozszerzenia VSIX?
 Począwszy od programu Visual Studio 2015, możesz nie należy instalować programu Visual Studio SDK z Centrum pobierania. Jest dołączony jako opcjonalna funkcja w Instalatorze programu Visual Studio. Możesz także zainstalować zestaw SDK programu VS później. Aby uzyskać więcej informacji, zobacz [instalacji programu Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).

## <a name="wheres-the-extension-documentation"></a>Gdzie znajduje się dokumentacja rozszerzenia?
 Rozpoczynać [do tworzenia rozszerzenia programu Visual Studio](../extensibility/starting-to-develop-visual-studio-extensions.md). Inne artykuły dotyczące programowania rozszerzeń VSSDK w witrynie MSDN są znajdujące się poniżej tego.

## <a name="can-i-convert-my-add-in-project-to-a-vsix-project"></a>Czy mogę przekonwertować mój projekt dodatku do projektu VSIX?
 Nie można przekonwertować projekt dodatku bezpośrednio do projektu VSIX, ponieważ mechanizm używany w projektów VSIX nie są takie same jak te w projektach dodatku. Szablon projektu VSIX, a także szablony elementów projektu mają duże ilości kodu, który sprawia, że stosunkowo łatwe rozpoczęcie korzystania i uruchomiony jako rozszerzenia VSIX.

##  <a name="BKMK_StartDeveloping"></a> Jak rozpocząć tworzenie rozszerzenia VSIX
 Poniżej przedstawiono, jak wprowadzić VSIX, który zawiera polecenie menu:

#### <a name="to-make-a-vsix-extension-that-has-a-menu-command"></a>Aby utworzyć rozszerzenie VSIX, który zawiera polecenie menu

1.  Utwórz projekt VSIX. (**Pliku** > **New** > **projektu**, lub typu **projektu** w **Szybkie uruchamianie** okno). W **nowy projekt** okna dialogowego rozwiń **Visual C#** > **rozszerzalności** lub **języka Visual Basic**  >   **Rozszerzalność** i wybierz **projekt VSIX**.) Nadaj projektowi nazwę **TestExtension** i określ lokalizację dla niego.

2.  Dodaj **polecenia niestandardowego** szablonu elementu projektu. (Kliknij prawym przyciskiem myszy węzeł projektu w **Eksploratora rozwiązań** i wybierz **Dodaj** > **nowy element**. W **nowy projekt** okno dialogowe dla programu Visual C# lub Visual Basic, wybierz **rozszerzalności** a następnie wybierz węzeł **polecenia niestandardowego**.)

3.  Naciśnij klawisz **F5** Aby skompilować i uruchomić projekt w trybie debugowania.

     Zostanie wyświetlone drugie wystąpienie programu Visual Studio. To drugie wystąpienie jest nazywany wystąpienie doświadczalne i może nie mieć tych samych ustawień co wystąpienie programu Visual Studio za pomocą pisania kodu. Podczas pierwszego uruchomienia wystąpienia eksperymentalnego użytkownik jest proszony logować się do usługi VS Online i określ motywu i profilu.

     Na **narzędzia** menu (w doświadczalnym wystąpieniu) powinien zostać wyświetlony przycisk o nazwie **nazwa polecenia Moje**. Po wybraniu tego przycisku, powinien pojawić się komunikat: **Inside TestVSPackagePackage.MenuItemCallback()**.

##  <a name="BKMK_RunAddin"></a> Jak mogę uruchomić Moje kodu dodatku w VSPackage
 Kodu dodatku jest zwykle uruchamiane w jednym z dwóch sposobów:

- Wyzwalane za pomocą polecenia menu (kod znajduje się w `IDTCommandTarget.Exec` metody.)

- Automatycznie podczas uruchamiania (kod znajduje się w `OnConnection` programu obsługi zdarzeń.)

  Możesz tworzyć tych samych czynności w VSPackage. Poniżej przedstawiono sposób dodawania kodu dodatku w metodzie wywołania zwrotnego:

### <a name="to-implement-a-menu-command-in-a-vspackage"></a>Implementowanie polecenia menu w VSPackage

1. Tworzenie pakietu VSPackage, który zawiera polecenie menu. (Aby uzyskać więcej informacji, zobacz [Tworzenie rozszerzenia za pomocą polecenia menu](../extensibility/creating-an-extension-with-a-menu-command.md).)

2. Otwórz plik, który zawiera definicję pakietu VSPackage. (W projekcie języka C# ma  *\<Nazwa projektu > Package.cs*.)

3. Dodaj następujący kod `using` instrukcje do pliku:

   ```csharp
   using EnvDTE;
   using EnvDTE80;
   ```

4. Znajdź `MenuItemCallback` metody. Dodaj wywołanie do <xref:Microsoft.VisualStudio.Shell.Package.GetService%2A> można pobrać <xref:EnvDTE80.DTE2> obiektu:

   ```csharp
   DTE2 dte = (DTE2)GetService(typeof(DTE));
   ```

5. Dodaj kod, który dodatku była w jego `IDTCommandTarget.Exec` metody. Na przykład poniżej przedstawiono niektóre kod, który dodaje nowe okienko do **dane wyjściowe** okno i wyświetla "Niektóre Text" w nowym okienku.

   ```csharp
   private void MenuItemCallback(object sender, EventArgs e)
   {
       DTE2 dte = (DTE2) GetService(typeof(DTE));
       OutputWindow outputWindow = dte.ToolWindows.OutputWindow;

       OutputWindowPane outputWindowPane = outputWindow.OutputWindowPanes.Add("A New Pane");
       outputWindowPane.OutputString("Some Text");
   }

   ```

6. Twórz i uruchamiaj tego projektu. Naciśnij klawisz **F5** lub wybierz **Start** na **debugowania** paska narzędzi. W doświadczalnym wystąpieniu programu Visual Studio **narzędzia** menu powinien mieć przycisk o nazwie **nazwa polecenia Moje**. Po wybraniu tego przycisku wyrazy **niektóre tekstu** powinna zostać wyświetlona w **dane wyjściowe** okienko. (Może być konieczne otwarcie **dane wyjściowe** okna.)

   Mogą też istnieć uruchomienia przy uruchamianiu kodu. To podejście zazwyczaj jest zalecane dla rozszerzenia pakietu VSPackage. Jeśli zbyt wiele rozszerzeń próbuje załadować po uruchomieniu programu Visual Studio, czas rozpoczęcia mogą stać się znacznie dłużej. Jest to lepsze rozwiązanie do automatycznego ładowania pakietu VSPackage, tylko wtedy, gdy spełniony jest jakiś warunek (np. rozwiązanie jest otwarte).

   Ta procedura pokazuje sposób uruchamiania kodu dodatku w pakietu VSPackage, który ładuje się automatycznie po otwarciu rozwiązania:

### <a name="to-autoload-a-vspackage"></a>Aby automatycznie załadować pakietu VSPackage

1. Utwórz projekt VSIX z elementem projektu pakietu Visual Studio. (Aby uzyskać instrukcje to zrobić, zobacz [jak rozpocząć tworzenie rozszerzeń VSIX?](../extensibility/faq-converting-add-ins-to-vspackage-extensions.md#BKMK_StartDeveloping). Wystarczy dodać atrybut **pakiet rozszerzeń Visual Studio** zamiast tego elementu projektu.) Nazwij projekt VSIX **TestAutoload**.

2. Otwórz *TestAutoloadPackage.cs*. Znajdź wiersz, w którym jest zadeklarowana w klasie pakietu:

   ```csharp
   public sealed class <name of your package>Package : Package
   ```

3. Powyżej tego wiersza to zestaw atrybutów. Dodaj ten atrybut:

   ```csharp
   [ProvideAutoLoad(UIContextGuids80.SolutionExists)]
   ```

4. Ustaw punkt przerwania `Initialize()` metody i rozpoczęcia debugowania (**F5**).

5. W doświadczalnym wystąpieniu Otwórz projekt. Pakietu VSPackage powinny zostać załadowane, a powinien trafiony punkt przerwania.

   Można określić innych kontekstach, w której chcesz załadować Twojego pakietu VSPackage przy użyciu pól <xref:Microsoft.VisualStudio.Shell.Interop.UIContextGuids80>. Aby uzyskać więcej informacji, zobacz [ładowanie pakietów VSPackage](../extensibility/loading-vspackages.md).

## <a name="how-can-i-get-the-dte-object"></a>Jak uzyskać obiekt DTE
 Jeśli dodatek nie powoduje wyświetlenia interfejsu użytkownika — na przykład, polecenia menu, przyciski paska narzędzi lub okna narzędzi — można użyć kodu jako — jest tak długo, jak pobrać obiektu automatyzacji DTE z pakietu VSPackage. Oto jak:

### <a name="to-get-the-dte-object-from-a-vspackage"></a>Aby uzyskać obiekt DTE z pakietu VSPackage

1. W projekcie VSIX z szablonem elementu pakiet rozszerzeń Visual Studio, wyszukaj  *\<Nazwa projektu > Package.cs* pliku. Jest to klasa, która pochodzi od klasy <xref:Microsoft.VisualStudio.Shell.Package>; może pomóc w interakcji z programem Visual Studio. W tym przypadku używasz jego <xref:Microsoft.VisualStudio.Shell.Package.GetService%2A> można pobrać <xref:EnvDTE80.DTE2> obiektu.

2. Dodaj następujące `using` instrukcji:

   ```csharp
   using EnvDTE;
   using EnvDTE80;
   ```

3. Znajdź `Initialize` metody. Ta metoda obsługuje polecenie, które określiłeś w kreatorze pakietu. Dodaj wywołanie do <xref:Microsoft.VisualStudio.Shell.Package.GetService%2A> można pobrać obiektu DTE:

   ```csharp
   DTE dte = (DTE)GetService(typeof(DTE));
   ```

   Po utworzeniu <xref:EnvDTE.DTE> obiektu automatyzacji, pozostała część kodu dodatku można dodać do projektu. Jeśli potrzebujesz <xref:EnvDTE80.DTE2> obiektu, możesz zrobić to samo.

## <a name="how-do-i-change-menu-commands-and-toolbar-buttons-in-my-add-in-to-the-vspackage-style"></a>Jak zmienić poleceń menu i przycisków paska narzędzi w mojej dodatku na VSPackage styl?
 Użyj rozszerzenia pakietu VSPackage *vsct* pliku w celu utworzenia większość poleceń menu, paski narzędzi, przyciski paska narzędzi i innych interfejsu użytkownika. **Polecenia niestandardowego** szablonu elementu projektu udostępnia opcję, aby utworzyć polecenie na **narzędzia** menu. Aby uzyskać więcej informacji, zobacz [Tworzenie rozszerzenia za pomocą polecenia menu](../extensibility/creating-an-extension-with-a-menu-command.md).

 Aby uzyskać więcej informacji na temat *vsct* plików, zobacz [VSPackages jak dodać elementy interfejsu użytkownika](../extensibility/internals/how-vspackages-add-user-interface-elements.md). Aby uzyskać wskazówki, które pokazują, jak używać *vsct* plik, aby dodać elementy menu, paski narzędzi i przyciski paska narzędzi, zobacz [rozszerzenia menu i poleceń](../extensibility/extending-menus-and-commands.md).

## <a name="how-do-i-add-custom-tool-windows-in-the-vspackage-way"></a>Jak dodać niestandardowe okna narzędzi w taki sposób, pakietu VSPackage?
 Okno narzędzia niestandardowego szablonu elementu projektu umożliwia utworzenie okna narzędzia. Aby uzyskać więcej informacji na temat tego szablonu elementu projektu, zobacz [Tworzenie rozszerzenia za pomocą okna narzędzia](../extensibility/creating-an-extension-with-a-tool-window.md). Uzyskać informacji o korzystaniu z okien narzędzi, zobacz [rozszerzanie i dostosowywanie okien narzędzi](../extensibility/extending-and-customizing-tool-windows.md) artykuły znajdujący się w nim szczególnie [Dodawanie okna narzędzi](../extensibility/adding-a-tool-window.md).

## <a name="how-do-i-manage-visual-studio-windows-in-the-vspackage-way"></a>Jak zarządzać okna programu Visual Studio w sposób pakietu VSPackage?
 Jeśli dodatek programu zarządza okna programu Visual Studio, kod dodatek powinien działać w VSPackage. Na przykład za pomocą poniższej procedury można dodać kod, który zarządza **listy zadań** do `MenuItemCallback` metoda pakietu VSPackage.

#### <a name="to-insert-window-management-code-from-an-add-in-into-a-vspackage"></a>Aby wstawić kod zarządzania systemem Windows z dodatek do VSPackage

1.  Tworzenie pakietu VSPackage, który zawiera polecenie menu, podobnie jak w [jak rozpocząć tworzenie rozszerzeń VSIX?](../extensibility/faq-converting-add-ins-to-vspackage-extensions.md#BKMK_StartDeveloping) sekcji.

2.  Otwórz plik, który zawiera definicję pakietu VSPackage. (W projekcie języka C# ma  *\<Nazwa projektu > Package.cs*.)

3.  Dodaj następujące `using` instrukcji:

    ```csharp
    using EnvDTE;
    using EnvDTE80;
    ```

4.  Znajdź `MenuItemCallback` metody. Dodaj wywołanie do <xref:Microsoft.VisualStudio.Shell.Package.GetService%2A> można pobrać <xref:EnvDTE80.DTE2> obiektu:

    ```csharp
    DTE2 dte = (DTE2)GetService(typeof(DTE));
    ```

5.  Dodawanie kodu za pomocą dodatku. Na przykład poniżej przedstawiono niektóre kod, który dodaje nowe zadania do **listy zadań**, wyświetla liczbę zadań, a następnie usuwa jedno zadanie.

    ```csharp
    private void MenuItemCallback(object sender, EventArgs e)
    {
        DTE2 dte = (DTE2) GetService(typeof(DTE));

        TaskList tl = (TaskList)dte.ToolWindows.TaskList;
        askItem tlItem;

        // Add a couple of tasks to the Task List.
        tlItem = tl.TaskItems.Add(" ", " ", "Test task 1.",
            vsTaskPriority.vsTaskPriorityHigh, vsTaskIcon.vsTaskIconUser,
            true, "", 10, true, true);
        tlItem = tl.TaskItems.Add(" ", " ", "Test task 2.",
            vsTaskPriority.vsTaskPriorityLow, vsTaskIcon.vsTaskIconComment, true, "", 20, true,true);

        // List the total number of task list items after adding the new task items.
        System.Windows.Forms.MessageBox.Show("Task Item 1 description: "+tl.TaskItems.Item(2).Description);
        System.Windows.Forms.MessageBox.Show("Total number of task items: "+tl.TaskItems.Count);

        // Remove the second task item. The items list in reverse numeric order.
        System.Windows.Forms.MessageBox.Show("Deleting the second task item");
        tl.TaskItems.Item(2).Delete();
        System.Windows.Forms.MessageBox.Show("Total number of task items: "+tl.TaskItems.Count);
    }
    ```

## <a name="how-do-i-manage-projects-and-solutions-in-a-vspackage"></a>Jak zarządzać projektami i rozwiązaniami w VSPackage
 Jeśli dodatek programu zarządza projekty i rozwiązania, kod dodatku powinien działać w VSPackage. Na przykład ta procedura pokazuje, jak dodać kod, który pobiera projekt startowy.

1.  Tworzenie pakietu VSPackage, który zawiera polecenie menu, podobnie jak w [jak rozpocząć tworzenie rozszerzeń VSIX?](../extensibility/faq-converting-add-ins-to-vspackage-extensions.md#BKMK_StartDeveloping) sekcji.

2.  Otwórz plik, który zawiera definicję pakietu VSPackage. (W projekcie języka C# ma  *\<Nazwa projektu > Package.cs*.)

3.  Dodaj następujące `using` instrukcji:

    ```csharp
    using EnvDTE;
    using EnvDTE80;
    ```

4.  Znajdź `MenuItemCallback` metody. Dodaj wywołanie do <xref:Microsoft.VisualStudio.Shell.Package.GetService%2A> można pobrać <xref:EnvDTE80.DTE2> obiektu:

    ```csharp
    DTE2 dte = (DTE2)GetService(typeof(DTE));
    ```

5.  Dodawanie kodu za pomocą dodatku. Na przykład poniższy kod umożliwia pobranie nazwy projektu startowego w rozwiązaniu. (Rozwiązanie z wieloma projektami musi być otwarty po uruchomieniu tego pakietu.)

    ```csharp
    private void MenuItemCallback(object sender, EventArgs e)
    {
        DTE2 dte = (DTE2) GetService(typeof(DTE));

        SolutionBuild2 sb = (SolutionBuild2)dte.Solution.SolutionBuild;
        Project startupProj;
        string msg = "";

        foreach (String item in (Array)sb.StartupProjects)
        {
            msg += item;
        }
        System.Windows.Forms.MessageBox.Show("Solution startup Project: "+msg);
        startupProj = dte.Solution.Item(msg);
        System.Windows.Forms.MessageBox.Show("Full name of solution's startup project: "+"/n"+startupProj.FullName);
    }
    ```

## <a name="how-do-i-set-keyboard-shortcuts-in-a-vspackage"></a>Jak ustawić skróty klawiaturowe w VSPackage?
 Możesz użyć `<KeyBindings>` elementu *vsct* pliku. W poniższym przykładzie skrótu klawiaturowego dla polecenia `idCommand1` jest **Alt**+**A**, a skrótu klawiaturowego dla polecenia `idCommand2` jest **Alt**  + **Ctrl**+**A**. Zwróć uwagę, składnia nazwy kluczy.

```xml
<KeyBindings>
    <KeyBinding guid="MyProjectCmdSet" id="idCommand1" editor="guidVSStd97" key1="A" mod1="ALT" />
    <KeyBinding guid="MyProjectCmdSet" id="idCommand2" editor="guidVSStd97" key1="A" mod1="CONTROL" mod2="ALT" />
</KeyBindings>
```

## <a name="how-do-i-handle-automation-events-in-a-vspackage"></a>Jak obsługiwać zdarzenia automatyzacji w VSPackage?
 Obsługa zdarzeń automatyzacji w VSPackage tak samo jak odbywa się tak jak w dodatku. Poniższy kod przedstawia sposób obsługi `OnItemRenamed` zdarzeń. (W tym przykładzie założono, że już trafiła do Ciebie obiekt DTE.)

```csharp
Events2 dteEvents = (Events2)dte.Events;
dteEvents.ProjectItemsEvents.ItemRenamed += listener1.OnItemRenamed;
. . .
public void OnItemRenamed(EnvDTE.ProjectItem projItem, string oldName)
{
    string s = "[Event] Renamed " + oldName + " to " + Path.GetFileName(projItem.get_FileNames(1) + " in project " + projItem.ContainingProject.Name;
}
```