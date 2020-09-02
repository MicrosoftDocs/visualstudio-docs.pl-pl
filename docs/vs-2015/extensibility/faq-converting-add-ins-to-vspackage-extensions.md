---
title: 'Często zadawane pytania: konwertowanie dodatków na rozszerzenia pakietu VSPackage | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
ms.assetid: 3a01d333-6e31-423f-ae06-5091a4fcb7a9
caps.latest.revision: 23
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: bc6ed31f96fc2021d0d9e104692f0440cfb78a5e
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "64821271"
---
# <a name="faq-converting-add-ins-to-vspackage-extensions"></a>Często zadawane pytania: konwertowanie dodatków na rozszerzenia pakietu VSPackage
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Dodatki są obecnie przestarzałe. Aby wykonać nowe rozszerzenie programu Visual Studio, należy utworzyć rozszerzenie VSIX. Poniżej znajdują się odpowiedzi na często zadawane pytania dotyczące sposobu konwersji dodatku programu Visual Studio na rozszerzenie VSIX.  
  
> [!WARNING]
> Począwszy od programu Visual Studio 2015, dla projektów C# i Visual Basic, można użyć projektu VSIX i dodać szablony elementów dla poleceń menu, okien narzędzi i pakietów VSPackage. Aby uzyskać więcej informacji, zobacz [co nowego w zestawie SDK programu Visual Studio 2015](../extensibility/what-s-new-in-the-visual-studio-2015-sdk.md).  
  
> [!IMPORTANT]
> W wielu przypadkach można po prostu przenieść kod dodatku do projektu VSIX z elementem projektu pakietu VSPackage. Obiekt automatyzacji DTE można uzyskać, wywołując <xref:Microsoft.VisualStudio.Shell.Package.GetService%2A> <xref:Microsoft.VisualStudio.Shell.Package.Initialize%2A> metodę.  
>   
> `DTE2 dte = (DTE2)GetService(typeof(DTE));`  
>   
> Aby uzyskać więcej informacji, zobacz [Jak mogę uruchomić kod dodatku w pakietu VSPackage?](../extensibility/faq-converting-add-ins-to-vspackage-extensions.md#BKMK_RunAddin) poniżej.  
  
## <a name="what-software-do-i-need-to-develop-vsix-extensions"></a>Jakie oprogramowanie jest potrzebne do opracowania rozszerzeń VSIX?  
 Począwszy od programu Visual Studio 2015, nie należy instalować zestawu Visual Studio SDK z centrum pobierania. Jest ona dostępna jako opcjonalna funkcja w Instalatorze programu Visual Studio. Zestaw VS SDK można także zainstalować później. Aby uzyskać więcej informacji, zobacz [Instalowanie zestawu Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).  
  
## <a name="wheres-the-extension-documentation"></a>Gdzie znajduje się dokumentacja rozszerzenia?  
 Zacznij od [rozpoczęcia tworzenia rozszerzeń programu Visual Studio](../extensibility/starting-to-develop-visual-studio-extensions.md). Inne artykuły dotyczące programowania rozszerzeń VSSDK w witrynie MSDN są poniżej tego.  
  
## <a name="can-i-convert-my-add-in-project-to-a-vsix-project"></a>Czy mogę przekonwertować mój projekt dodatku do projektu VSIX?  
 Projekt dodatku nie może zostać skonwertowany bezpośrednio do projektu VSIX, ponieważ mechanizmy używane w projektach VSIX nie są takie same jak te w projektach dodatków. Szablon projektu VSIX oraz odpowiednie szablony elementów projektu zawierają wiele kodów, które znacznie ułatwiają rozpoczęcie pracy jako rozszerzenie VSIX.  
  
## <a name="how-do-i-start-developing-vsix-extensions"></a><a name="BKMK_StartDeveloping"></a> Jak mogę rozpocząć opracowywanie rozszerzeń VSIX?  
 Oto jak utworzyć VSIX z poleceniem menu:  
  
#### <a name="to-make-a-vsix-extension-that-has-a-menu-command"></a>Aby utworzyć rozszerzenie VSIX, które ma polecenie menu  
  
1. Utwórz projekt VSIX. (**Plik**, **Nowy**, **projekt**lub typ **projektu** w oknie **Szybkie uruchamianie** ). W oknie dialogowym **Nowy projekt** rozwiń węzeł **Visual C#/rozszerzalność** lub **Visual Basic/rozszerzalność** i wybierz **Projekt VSIX**.) Nadaj projektowi nazwę **TestExtension** i określ dla niego lokalizację.  
  
2. Dodaj niestandardowy szablon elementu projektu **polecenia** . (Kliknij prawym przyciskiem myszy węzeł projektu w **Eksplorator rozwiązań** i wybierz polecenie **Dodaj/nowy element**. W oknie dialogowym **Nowy projekt** dla Visual C# lub Visual Basic wybierz węzeł **rozszerzalności** i wybierz **polecenie niestandardowe**.)  
  
3. Naciśnij klawisz F5, aby skompilować i uruchomić projekt w trybie debugowania.  
  
     Zostanie wyświetlone drugie wystąpienie programu Visual Studio. Drugie wystąpienie jest nazywane wystąpieniem eksperymentalnym i może nie mieć takich samych ustawień jak wystąpienie programu Visual Studio, którego używasz do pisania kodu. Przy pierwszym uruchomieniu eksperymentalnego wystąpienia zostanie wyświetlony monit o zalogowanie do usługi VS Online i określenie motywu i profilu.  
  
     W menu **Narzędzia** (w eksperymentalnym wystąpieniu) powinien zostać wyświetlony przycisk o nazwie **My Command**. Po wybraniu tego przycisku powinien pojawić się komunikat: **wewnątrz TestVSPackagePackage. MenuItemCallback ()**.  
  
## <a name="how-can-i-run-my-add-in-code-in-a-vspackage"></a><a name="BKMK_RunAddin"></a> Jak mogę uruchomić kod dodatku w pakietu VSPackage?  
 Kod dodatku jest zwykle uruchamiany na jeden z dwóch sposobów:  
  
- Wyzwolone przez polecenie menu (kod jest w `IDTCommandTarget.Exec` metodzie)  
  
- Automatycznie przy uruchamianiu (kod znajduje się w `OnConnection` obsłudze zdarzeń).  
  
  Te same elementy można wykonać w pakietu VSPackage. Poniżej przedstawiono sposób dodawania kodu dodatku w metodzie wywołania zwrotnego:  
  
#### <a name="to-implement-a-menu-command-in-a-vspackage"></a>Aby zaimplementować polecenie menu w pakietu VSPackage  
  
1. Utwórz element pakietu VSPackage, który ma polecenie menu. (Aby uzyskać więcej informacji, zobacz [Tworzenie rozszerzenia za pomocą polecenia menu](../extensibility/creating-an-extension-with-a-menu-command.md)).  
  
2. Otwórz plik, który zawiera definicję pakietu VSPackage. (W projekcie języka C# jest <em>\<your project name></em> to Package.cs.)  
  
3. Dodaj następujące `using` instrukcje do pliku:  
  
   ```csharp  
   using EnvDTE;  
   using EnvDTE80;  
   ```  
  
4. Znajdź `MenuItemCallback` metodę. Dodaj wywołanie w <xref:Microsoft.VisualStudio.Shell.Package.GetService%2A> celu pobrania <xref:EnvDTE80.DTE2> obiektu:  
  
   ```csharp  
   DTE2 dte = (DTE2)GetService(typeof(DTE));  
   ```  
  
5. Dodaj kod, którego dodatek miał w swojej `IDTCommandTarget.Exec` metodzie. Na przykład Oto kod, który dodaje nowe okienko do okna **dane wyjściowe** i drukuje tekst "część tekstu" w nowym okienku.  
  
   ```csharp  
   private void MenuItemCallback(object sender, EventArgs e)  
   {  
       DTE2 dte = (DTE2) GetService(typeof(DTE));  
       OutputWindow outputWindow = dte.ToolWindows.OutputWindow;  
  
       OutputWindowPane outputWindowPane = outputWindow.OutputWindowPanes.Add("A New Pane");  
       outputWindowPane.OutputString("Some Text");  
   }  
  
   ```  
  
6. Kompiluj i uruchamiaj ten projekt. Naciśnij klawisz F5 lub wybierz pozycję **Rozpocznij** na pasku narzędzi **debugowania** . W eksperymentalnym wystąpieniu programu Visual Studio menu **Tools** powinno mieć przycisk o nazwie **My Command**. Po wybraniu tego przycisku, w okienku okna **dane wyjściowe** powinny pojawić się **niektóre teksty** . (Może być konieczne otwarcie okna **dane wyjściowe** ).  
  
   Kod można także uruchomić przy uruchamianiu. Jednak takie podejście jest ogólnie odradzane w przypadku rozszerzeń pakietu VSPackage. Jeśli zbyt wiele rozszerzeń spróbuje załadować po rozpoczęciu programu Visual Studio, czas rozpoczęcia może się znacznie wydłużyć. Lepszym rozwiązaniem jest załadowanie pakietu VSPackage automatycznie tylko wtedy, gdy spełniony jest jakiś warunek (na przykład otwarte rozwiązanie).  
  
   Ta procedura pokazuje, jak uruchomić kod dodatku w pakietu VSPackage, który ładuje się automatycznie podczas otwierania rozwiązania:  
  
#### <a name="to-autoload-a-vspackage"></a>Aby załadować pakietu VSPackage  
  
1. Utwórz projekt VSIX z elementem projektu pakietu programu Visual Studio. (Aby uzyskać instrukcje, zobacz [Jak mogę rozpocząć opracowywanie rozszerzeń VSIX?](../extensibility/faq-converting-add-ins-to-vspackage-extensions.md#BKMK_StartDeveloping). Wystarczy dodać element projektu **pakietu programu Visual Studio** ). Nadaj nazwę projektowi VSIX **TestAutoload**.  
  
2. Otwórz TestAutoloadPackage.cs. Znajdź wiersz, w którym zadeklarowana jest Klasa pakietu:  
  
   ```csharp  
   public sealed class <name of your package>Package : Package  
   ```  
  
3. Powyżej ten wiersz jest zestawem atrybutów. Dodaj ten atrybut:  
  
   ```csharp  
   [ProvideAutoLoad(UIContextGuids80.SolutionExists)]  
   ```  
  
4. Ustaw punkt przerwania w `Initialize()` metodzie i Rozpocznij debugowanie (F5).  
  
5. W eksperymentalnym wystąpieniu Otwórz projekt. Pakietu VSPackage powinny ładować i punkt przerwania powinien zostać trafiony.  
  
   Można określić inne konteksty, w których można załadować pakietu VSPackage przy użyciu pól <xref:Microsoft.VisualStudio.Shell.Interop.UIContextGuids80> . Aby uzyskać więcej informacji, zobacz [ładowanie pakietów VSPackage](../extensibility/loading-vspackages.md).  
  
## <a name="how-can-i-get-the-dte-object"></a>Jak uzyskać obiekt DTE?  
 Jeśli w dodatku nie jest wyświetlany interfejs użytkownika — na przykład polecenia menu, przyciski paska narzędzi lub okna narzędzi — może być możliwe użycie kodu w taki sam sposób, jak obiekt automatyzacji DTE z pakietu VSPackage. Oto kroki tej procedury:  
  
#### <a name="to-get-the-dte-object-from-a-vspackage"></a>Aby uzyskać obiekt DTE z pakietu VSPackage  
  
1. W projekcie VSIX z szablonem elementu pakietu Visual Studio Znajdź <em>\<project name></em> plik Package.cs. Jest to Klasa, która pochodzi od <xref:Microsoft.VisualStudio.Shell.Package> ; może pomóc w współpracy z programem Visual Studio. W takim przypadku należy użyć jego <xref:Microsoft.VisualStudio.Shell.Package.GetService%2A> do pobrania <xref:EnvDTE80.DTE2> obiektu.  
  
2. Dodaj następujące `using` instrukcje:  
  
   ```csharp  
   using EnvDTE;  
   using EnvDTE80;  
   ```  
  
3. Znajdź `Initialize` metodę. Ta metoda obsługuje polecenie określone w Kreatorze pakietu. Dodaj wywołanie w <xref:Microsoft.VisualStudio.Shell.Package.GetService%2A> celu pobrania obiektu DTE:  
  
   ```csharp  
   DTE dte = (DTE)GetService(typeof(DTE));  
   ```  
  
   Po utworzeniu <xref:EnvDTE.DTE> obiektu automatyzacji możesz dodać resztę kodu dodatku do projektu. Jeśli potrzebujesz <xref:EnvDTE80.DTE2> obiektu, możesz to zrobić w ten sam sposób.  
  
## <a name="how-do-i-change-menu-commands-and-toolbar-buttons-in-my-add-in-to-the-vspackage-style"></a>Jak mogę zmienić polecenia menu i przyciski paska narzędzi w moim dodatku do stylu pakietu VSPackage?  
 Rozszerzenia pakietu VSPackage korzystają z pliku. vsct w celu utworzenia większości poleceń menu, pasków narzędzi, przycisków i innych interfejsów użytkownika. Szablon elementu projektu **polecenia niestandardowego** udostępnia opcję tworzenia polecenia w menu **Narzędzia** . Aby uzyskać więcej informacji, zobacz [Tworzenie rozszerzenia za pomocą polecenia menu](../extensibility/creating-an-extension-with-a-menu-command.md).  
  
 Aby uzyskać więcej informacji na temat plików. vsct, zobacz [jak pakietów VSPackage dodać elementy interfejsu użytkownika](../extensibility/internals/how-vspackages-add-user-interface-elements.md). Przewodniki pokazujące, jak używać pliku. vsct do dodawania elementów menu, pasków narzędzi i przycisków paska narzędzi, zobacz [rozszerzanie menu i poleceń](../extensibility/extending-menus-and-commands.md).  
  
## <a name="how-do-i-add-custom-tool-windows-in-the-vspackage-way"></a>Jak mogę dodać niestandardowe okna narzędzi w pakietu VSPackage sposób?  
 Szablon elementu projektu niestandardowego okna narzędzi udostępnia opcję tworzenia okna narzędzi. Aby uzyskać więcej informacji na temat tego szablonu elementu projektu, zobacz [Tworzenie rozszerzenia przy użyciu okna narzędzi](../extensibility/creating-an-extension-with-a-tool-window.md). Aby uzyskać informacje o oknach narzędzi, zobacz [rozszerzanie i dostosowywanie okien narzędzi](../extensibility/extending-and-customizing-tool-windows.md) i artykułów w nich, zwłaszcza [dodanie okna narzędzi](../extensibility/adding-a-tool-window.md).  
  
## <a name="how-do-i-manage-visual-studio-windows-in-the-vspackage-way"></a>Jak mogę zarządzać oknami programu Visual Studio w pakietu VSPackage sposób?  
 Jeśli dodatek zarządza oknami programu Visual Studio, kod dodatku powinien być działał w pakietu VSPackage. Na przykład ta procedura pokazuje, jak dodać kod zarządzający **Lista zadań** do `MenuItemCallback` metody pakietu VSPackage.  
  
#### <a name="to-insert-window-management-code-from-an-add-in-into-a-vspackage"></a>Aby wstawić kod zarządzania oknem z dodatku do pakietu VSPackage  
  
1. Utwórz element pakietu VSPackage, który zawiera polecenie menu, jak w [Jak mogę rozpocząć opracowywanie rozszerzeń VSIX?](../extensibility/faq-converting-add-ins-to-vspackage-extensions.md#BKMK_StartDeveloping)  
  
2. Otwórz plik, który zawiera definicję pakietu VSPackage. (W projekcie języka C# jest <em>\<your project name></em> to Package.cs.)  
  
3. Dodaj następujące `using` instrukcje:  
  
   ```csharp  
   using EnvDTE;  
   using EnvDTE80;  
   ```  
  
4. Znajdź `MenuItemCallback` metodę. Dodaj wywołanie w <xref:Microsoft.VisualStudio.Shell.Package.GetService%2A> celu pobrania <xref:EnvDTE80.DTE2> obiektu:  
  
   ```csharp  
   DTE2 dte = (DTE2)GetService(typeof(DTE));  
   ```  
  
5. Dodaj kod z dodatku. Na przykład Oto kod, który dodaje nowe zadania do **Lista zadań**, wyświetla liczbę zadań, a następnie usuwa jedno zadanie.  
  
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
  
## <a name="how-do-i-manage-projects-and-solutions-in-a-vspackage"></a>Jak mogę zarządzać projektami i rozwiązaniami w pakietu VSPackage?  
 Jeśli dodatek zarządza projektami i rozwiązaniami, kod dodatku powinien być działał w pakietu VSPackage. Na przykład ta procedura pokazuje, jak dodać kod, który pobiera projekt startowy.  
  
1. Utwórz element pakietu VSPackage, który zawiera polecenie menu, jak w [Jak mogę rozpocząć opracowywanie rozszerzeń VSIX?](../extensibility/faq-converting-add-ins-to-vspackage-extensions.md#BKMK_StartDeveloping)  
  
2. Otwórz plik, który zawiera definicję pakietu VSPackage. (W projekcie języka C# jest <em>\<your project name></em> to Package.cs.)  
  
3. Dodaj następujące `using` instrukcje:  
  
   ```csharp  
   using EnvDTE;  
   using EnvDTE80;  
   ```  
  
4. Znajdź `MenuItemCallback` metodę. Dodaj wywołanie w <xref:Microsoft.VisualStudio.Shell.Package.GetService%2A> celu pobrania <xref:EnvDTE80.DTE2> obiektu:  
  
   ```csharp  
   DTE2 dte = (DTE2)GetService(typeof(DTE));  
   ```  
  
5. Dodaj kod z dodatku. Na przykład poniższy kod pobiera nazwę projektu startowego w rozwiązaniu. (W przypadku uruchomienia tego pakietu należy otworzyć rozwiązanie wieloprojektowe).  
  
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
  
## <a name="how-do-i-set-keyboard-shortcuts-in-a-vspackage"></a>Jak mogę ustawić skróty klawiaturowe w pakietu VSPackage?  
 Używasz `<KeyBindings>` elementu pliku. vsct. W poniższym przykładzie skrót klawiaturowy polecenia `idCommand1` jest Alt + A, a skrót klawiaturowy dla polecenia `idCommand2` to Alt + Ctrl + A. Zwróć uwagę na składnię nazw kluczy.  
  
```xml  
<KeyBindings>  
    <KeyBinding guid="MyProjectCmdSet" id="idCommand1" editor="guidVSStd97" key1="A" mod1="ALT" />  
    <KeyBinding guid="MyProjectCmdSet" id="idCommand2" editor="guidVSStd97" key1="A" mod1="CONTROL" mod2="ALT" />  
</KeyBindings>  
```  
  
## <a name="how-do-i-handle-automation-events-in-a-vspackage"></a>Jak mogę obsłużyć zdarzenia automatyzacji w pakietu VSPackage?  
 Zdarzenia automatyzacji można obsłużyć w pakietu VSPackage w taki sam sposób jak w dodatku. Poniższy kod pokazuje, jak obsłużyć `OnItemRenamed` zdarzenie. (W tym przykładzie przyjęto założenie, że już masz obiekt DTE).  
  
```csharp  
Events2 dteEvents = (Events2)dte.Events;  
dteEvents.ProjectItemsEvents.ItemRenamed += listener1.OnItemRenamed;   
. . .  
public void OnItemRenamed(EnvDTE.ProjectItem projItem, string oldName)   
{  
    string s = "[Event] Renamed " + oldName + " to " + Path.GetFileName(projItem.get_FileNames(1) + " in project " + projItem.ContainingProject.Name;   
}  
```
