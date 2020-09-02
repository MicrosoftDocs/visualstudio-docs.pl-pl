---
title: Zarządzanie projektami uniwersalnymi systemu Windows | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
ms.assetid: 47926aa1-3b41-410d-bca8-f77fc950cbe7
caps.latest.revision: 15
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 08d88ce08c6c91cbf46bcc6d15cbf098d61e604d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "65679932"
---
# <a name="managing-universal-windows-projects"></a>Zarządzanie uniwersalnymi projektami systemu Windows
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Aplikacje uniwersalne systemu Windows to aplikacje przeznaczone zarówno dla Windows 8.1, jak i Windows Phone 8,1, dzięki czemu deweloperzy mogą korzystać z kodu i innych zasobów na obu platformach. Udostępniony kod i zasoby są przechowywane w projekcie udostępnionym, podczas gdy kod i zasoby specyficzne dla platformy są przechowywane w oddzielnych projektach, jeden dla systemu Windows, a drugi dla Windows Phone. Aby uzyskać więcej informacji na temat uniwersalnych aplikacji systemu Windows, zobacz [aplikacje uniwersalne systemu Windows](https://msdn.microsoft.com/library/windows/apps/dn609832.aspx). Rozszerzenia programu Visual Studio, które zarządzają projektami, powinny mieć świadomość, że projekty aplikacji uniwersalnych systemu Windows mają strukturę, która różni się od aplikacji jednoplatformowych. W tym instruktażu pokazano, jak nawigować po projekcie udostępnionym i zarządzać elementami udostępnionymi.  
  
## <a name="prerequisites"></a>Wymagania wstępne  
 Począwszy od programu Visual Studio 2015, nie należy instalować zestawu Visual Studio SDK z centrum pobierania. Jest ona dostępna jako opcjonalna funkcja w Instalatorze programu Visual Studio. Zestaw VS SDK można także zainstalować później. Aby uzyskać więcej informacji, zobacz [Instalowanie zestawu Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).  
  
### <a name="navigate-the-shared-project"></a>Nawigowanie po projekcie udostępnionym  
  
1. Utwórz projekt w języku C# o nazwie **TestUniversalProject**. (**Plik, nowy, projekt** , a następnie **C#, rozszerzalność, pakiet Visual Studio**). Dodaj **niestandardowy** szablon elementu projektu polecenia (na Eksplorator rozwiązań kliknij prawym przyciskiem myszy węzeł projektu i wybierz polecenie **Dodaj/nowy element**, a następnie przejdź do obszaru **rozszerzalności**). Nazwij plik **TestUniversalProject**.  
  
2. Dodaj odwołanie do Microsoft.VisualStudio.Shell.Interop.12.1.DesignTime.dll i Microsoft.VisualStudio.Shell.Interop.14.0.DesignTime.dll (w sekcji **rozszerzenia** ).  
  
3. Otwórz TestUniversalProject.cs i Dodaj następujące `using` instrukcje:  
  
    ```csharp  
    using EnvDTE;  
    using EnvDTE80;  
    using Microsoft.VisualStudio;  
    using Microsoft.VisualStudio.PlatformUI;  
    using Microsoft.Internal.VisualStudio.PlatformUI;   
    using System.Collections.Generic;   
    using System.IO;  
    using System.Windows.Forms;  
    ```  
  
4. W klasie TestUniversalProject Dodaj pole private wskazujące okno **dane wyjściowe** .  
  
    ```csharp  
    public sealed class TestUniversalProject   
    {  
        IVsOutputWindowPane output;  
    . . .  
    }  
    ```  
  
5. Ustaw odwołanie do okienka danych wyjściowych w konstruktorze TestUniversalProject:  
  
    ```csharp  
    private TestUniversalProject(Package package)  
    {  
        if (package == null)  
        {  
            throw new ArgumentNullException("package");  
        }  
  
        this.package = package;  
  
        OleMenuCommandService commandService = this.ServiceProvider.GetService(typeof(IMenuCommandService)) as OleMenuCommandService;  
        if (commandService != null)  
        {  
            CommandID menuCommandID = new CommandID(MenuGroup, CommandId);  
            EventHandler eventHandler = this.ShowMessageBox;  
            MenuCommand menuItem = new MenuCommand(eventHandler, menuCommandID);  
            commandService.AddCommand(menuItem);  
        }  
        // get a reference to the Output window  
                    output = (IVsOutputWindowPane)ServiceProvider.GetService(typeof(SVsGeneralOutputWindowPane));  
    }  
    ```  
  
6. Usuń istniejący kod z `ShowMessageBox` metody:  
  
    ```csharp  
    private void ShowMessageBox(object sender, EventArgs e)   
    {  
    }  
    ```  
  
7. Pobierz obiekt DTE, który będzie używany w kilku różnych celach w tym instruktażu. Upewnij się również, że rozwiązanie zostało załadowane po kliknięciu przycisku menu.  
  
    ```csharp  
    private void ShowMessageBox(object sender, EventArgs e)  
    {   
        var dte = (EnvDTE.DTE)this.ServiceProvider.GetService(typeof(EnvDTE.DTE));  
        if (dte.Solution != null)   
        {  
            . . .  
        }  
        else   
        {  
            MessageBox.Show("No solution is open");  
            return;   
        }  
    }  
    ```  
  
8. Znajdź projekt udostępniony. Udostępniony projekt jest czystym kontenerem; nie kompiluje ani nie tworzy danych wyjściowych. Poniższa metoda umożliwia znalezienie pierwszego udostępnionego projektu w rozwiązaniu przez wyszukanie <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> obiektu, który ma możliwość projektu udostępnionego.  
  
    ```csharp  
    private IVsHierarchy FindSharedProject()  
    {  
        var sln = (IVsSolution)this.ServiceProvider.GetService(typeof(SVsSolution));  
        Guid empty = Guid.Empty;  
        IEnumHierarchies enumHiers;  
  
        //get all the projects in the solution  
        ErrorHandler.ThrowOnFailure(sln.GetProjectEnum((uint)__VSENUMPROJFLAGS.EPF_LOADEDINSOLUTION, ref empty, out enumHiers));  
        foreach (IVsHierarchy hier in ComUtilities.EnumerableFrom(enumHiers))  
        {  
            if (PackageUtilities.IsCapabilityMatch(hier, "SharedAssetsProject"))  
            {  
                return hier;  
            }  
        }  
        return null;  
    }  
    ```  
  
9. W `ShowMessageBox` metodzie dane wyjściowe podpisu (nazwa projektu, który pojawia się w **Eksplorator rozwiązań**) projektu udostępnionego.  
  
    ```csharp  
    private void ShowMessageBox(object sender, EventArgs e)  
    {  
        var dte = (DTE)this.ServiceProvider.GetService(typeof(DTE));  
  
        if (dte.Solution != null)  
        {  
            var sharedHier = this.FindSharedProject();  
            if (sharedHier != null)  
            {  
                string sharedCaption = HierarchyUtilities.GetHierarchyProperty<string>(sharedHier, (uint)VSConstants.VSITEMID.Root,  
                     (int)__VSHPROPID.VSHPROPID_Caption);  
                output.OutputStringThreadSafe(string.Format("Found shared project: {0}\n", sharedCaption));  
            }  
            else  
            {  
                MessageBox.Show("Solution has no shared project");  
                return;  
            }  
                }  
        else  
        {  
            MessageBox.Show("No solution is open");  
            return;  
        }  
    }  
    ```  
  
10. Pobierz aktywny projekt platformy. Projekty platformy to projekty, które zawierają kod i zasoby specyficzne dla platformy. Poniższa metoda używa nowego pola <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID7> do uzyskania aktywnego projektu platformy.  
  
    ```csharp  
    private IVsHierarchy GetActiveProjectContext(IVsHierarchy hierarchy)  
    {  
        IVsHierarchy activeProjectContext;  
        if (HierarchyUtilities.TryGetHierarchyProperty(hierarchy, (uint)VSConstants.VSITEMID.Root,  
             (int)__VSHPROPID7.VSHPROPID_SharedItemContextHierarchy, out activeProjectContext))  
        {  
            return activeProjectContext;  
        }  
        else  
        {  
            return null;  
        }  
    }  
    ```  
  
11. W `ShowMessageBox` metodzie dane wyjściowe mają podpis aktywnego projektu platformy.  
  
    ```csharp  
    private void ShowMessageBox(object sender, EventArgs e)  
    {  
        var dte = (DTE)this.ServiceProvider.GetService(typeof(DTE));  
  
        if (dte.Solution != null)  
        {  
            var sharedHier = this.FindSharedProject();  
            if (sharedHier != null)  
            {  
                string sharedCaption = HierarchyUtilities.GetHierarchyProperty<string>(sharedHier, (uint)VSConstants.VSITEMID.Root,  
                     (int)__VSHPROPID.VSHPROPID_Caption);  
                output.OutputStringThreadSafe(string.Format("Shared project: {0}\n", sharedCaption));  
  
                var activePlatformHier = this.GetActiveProjectContext(sharedHier);  
                if (activePlatformHier != null)  
                {  
                    string activeCaption = HierarchyUtilities.GetHierarchyProperty<string>(activePlatformHier,  
                         (uint)VSConstants.VSITEMID.Root, (int)__VSHPROPID.VSHPROPID_Caption);  
                    output.OutputStringThreadSafe(string.Format("Active platform project: {0}\n", activeCaption));  
                }  
                else  
                {  
                MessageBox.Show("Shared project has no active platform project");  
                }  
            }  
            else  
            {  
                MessageBox.Show("Solution has no shared project");  
                return;  
            }  
        }  
        else  
            {  
                MessageBox.Show("No solution is open");  
                return;  
            }  
        }  
  
    ```  
  
12. Wykonaj iterację projektów platformy. Poniższa metoda pobiera wszystkie projekty importowania (platformy) z projektu udostępnionego.  
  
    ```csharp  
    private IEnumerable<IVsHierarchy> EnumImportingProjects(IVsHierarchy hierarchy)  
    {  
        IVsSharedAssetsProject sharedAssetsProject;  
        if (HierarchyUtilities.TryGetHierarchyProperty(hierarchy, (uint)VSConstants.VSITEMID.Root,  
            (int)__VSHPROPID7.VSHPROPID_SharedAssetsProject, out sharedAssetsProject)  
            && sharedAssetsProject != null)  
        {  
            foreach (IVsHierarchy importingProject in sharedAssetsProject.EnumImportingProjects())  
            {  
                yield return importingProject;  
            }  
        }  
    }  
    ```  
  
    > [!IMPORTANT]
    > Jeśli użytkownik otworzył projekt uniwersalnej aplikacji systemu Windows w języku C++ w eksperymentalnym wystąpieniu, kod powyżej zgłasza wyjątek. Jest to znany problem. Aby uniknąć wyjątku, Zastąp `foreach` blok powyżej następującym:  
  
    ```csharp  
    var importingProjects = sharedAssetsProject.EnumImportingProjects();  
    for (int i = 0; i < importingProjects.Count; ++i)  
    {  
        yield return importingProjects[i];  
    }   
    ```  
  
13. W `ShowMessageBox` metodzie dane wyjściowe są wyświetlane na końcu podpisu każdego projektu platformy. Wstaw poniższy kod po wierszu, który wyprowadza podpis aktywnego projektu platformy. Na tej liście są wyświetlane tylko te projekty platformy, które zostały załadowane.  
  
    ```csharp  
    output.OutputStringThreadSafe("Platform projects:\n");  
  
    IEnumerable<IVsHierarchy> projects = this.EnumImportingProjects(sharedHier);  
  
    bool isActiveProjectSet = false;  
    foreach (IVsHierarchy platformHier in projects)  
    {  
        string platformCaption = HierarchyUtilities.GetHierarchyProperty<string>(platformHier, (uint)VSConstants.VSITEMID.Root,  
            (int)__VSHPROPID.VSHPROPID_Caption);  
        output.OutputStringThreadSafe(string.Format(" * {0}\n", platformCaption));  
    }  
    ```  
  
14. Zmień aktywny projekt platformy. Poniższa metoda ustawia aktywny projekt przy użyciu <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.SetProperty%2A> .  
  
    ```csharp  
    private int SetActiveProjectContext(IVsHierarchy hierarchy, IVsHierarchy activeProjectContext)  
    {  
        return hierarchy.SetProperty((uint)VSConstants.VSITEMID.Root, (int)__VSHPROPID7.VSHPROPID_SharedItemContextHierarchy, activeProjectContext);  
    }  
    ```  
  
15. W `ShowMessageBox` metodzie Zmień aktywny projekt platformy. Wstaw ten kod wewnątrz `foreach` bloku.  
  
    ```csharp  
    bool isActiveProjectSet = false;  
    string platformCaption = null;  
    foreach (IVsHierarchy platformHier in projects)  
    {  
        platformCaption = HierarchyUtilities.GetHierarchyProperty<string>(platformHier, (uint)VSConstants.VSITEMID.Root,  
             (int)__VSHPROPID.VSHPROPID_Caption);  
        output.OutputStringThreadSafe(string.Format(" * {0}\n", platformCaption));  
  
        // if this project is neither the shared project nor the current active platform project,   
        // set it to be the active project  
        if (!isActiveProjectSet && platformHier != activePlatformHier)  
        {  
            this.SetActiveProjectContext(sharedHier, platformHier);  
            activePlatformHier = platformHier;  
            isActiveProjectSet = true;  
        }  
    }  
    output.OutputStringThreadSafe("set active project: " + platformCaption +'\n');  
    ```  
  
16. Wypróbuj teraz. Naciśnij klawisz F5, aby uruchomić wystąpienie eksperymentalne. Tworzenie projektu aplikacji uniwersalnej w języku C# w eksperymentalnym wystąpieniu (w oknie dialogowym **Nowy projekt** , **Visual C#/Windows/Windows 8/Aplikacje uniwersalne/centralne**). Po załadowaniu rozwiązania przejdź do menu **Narzędzia** , a następnie kliknij pozycję **Wywołaj TestUniversalProject**, a następnie sprawdź tekst w okienku **dane wyjściowe** . Powinna zostać wyświetlona zawartość podobna do tej:  
  
    ```  
    Found shared project: HubApp.Shared  
    The active platform project: HubApp.Windows  
    Platform projects:  
     * HubApp.Windows  
     * HubApp.WindowsPhone  
    set active project: HubApp.WindowsPhone  
    ```  
  
### <a name="manage-the-shared-items-in-the-platform-project"></a>Zarządzanie elementami udostępnionymi w projekcie platformy  
  
1. Znajdź elementy udostępnione w projekcie platformy. Elementy w projekcie udostępnionym są wyświetlane w projekcie platformy jako elementy udostępnione. Nie są one widoczne w **Eksplorator rozwiązań**, ale można przeszukać hierarchię projektu, aby je znaleźć. Poniższa metoda przeprowadzi hierarchię i gromadzi wszystkie elementy udostępnione. Opcjonalnie zwraca podpis każdego elementu,. Elementy udostępnione są identyfikowane przez nową właściwość <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID7> .  
  
    ```csharp  
    private void InspectHierarchyItems(IVsHierarchy hier, uint itemid, int level, List<uint> itemIds, bool getSharedItems, bool printItems)  
    {  
        string caption = HierarchyUtilities.GetHierarchyProperty<string>(hier, itemid, (int)__VSHPROPID.VSHPROPID_Caption);  
        if (printItems)  
            output.OutputStringThreadSafe(string.Format("{0}{1}\n", new string('\t', level), caption));  
  
        // if getSharedItems is true, inspect only shared items; if it's false, inspect only unshared items  
        bool isSharedItem;  
        if (HierarchyUtilities.TryGetHierarchyProperty(hier, itemid, (int)__VSHPROPID7.VSHPROPID_IsSharedItem, out isSharedItem)  
            && (isSharedItem == getSharedItems))  
        {  
            itemIds.Add(itemid);  
        }  
  
        uint child;  
        if (HierarchyUtilities.TryGetHierarchyProperty(hier, itemid, (int)__VSHPROPID.VSHPROPID_FirstChild, Unbox.AsUInt32, out child)  
            && child != (uint)VSConstants.VSITEMID.Nil)  
        {  
            this.InspectHierarchyItems(hier, child, level + 1, itemIds, isSharedItem, printItems);  
  
            while (HierarchyUtilities.TryGetHierarchyProperty(hier, child, (int)__VSHPROPID.VSHPROPID_NextSibling, Unbox.AsUInt32, out child)  
                && child != (uint)VSConstants.VSITEMID.Nil)  
            {  
                this.InspectHierarchyItems(hier, child, level + 1, itemIds, isSharedItem, printItems);  
            }  
                    }  
    }  
    ```  
  
2. W `ShowMessageBox` metodzie Dodaj następujący kod, aby przeprowadzić elementy hierarchii projektu platformy. Wstaw ją wewnątrz `foreach` bloku.  
  
    ```csharp  
    output.OutputStringThreadSafe("Walk the active platform project:\n");  
    var sharedItemIds = new List<uint>();  
    this.InspectHierarchyItems(activePlatformHier, (uint)VSConstants.VSITEMID.Root, 1, sharedItemIds, true, true);  
    ```  
  
3. Odczytaj elementy udostępnione. Elementy udostępnione są wyświetlane w projekcie platformy jako ukryte pliki połączone i można odczytywać wszystkie właściwości jako zwykłe pliki połączone. Poniższy kod odczytuje pełną ścieżkę pierwszego elementu udostępnionego.  
  
    ```csharp  
    var sharedItemId = sharedItemIds[0];  
    string fullPath;  
    ErrorHandler.ThrowOnFailure(((IVsProject)activePlatformHier).GetMkDocument(sharedItemId, out fullPath));  
    output.OutputStringThreadSafe(string.Format("Shared item full path: {0}\n", fullPath));  
    ```  
  
4. Wypróbuj teraz. Naciśnij klawisz F5, aby uruchomić wystąpienie eksperymentalne. Tworzenie projektu aplikacji uniwersalnej w języku C# w eksperymentalnym wystąpieniu (w oknie dialogowym **Nowy projekt** , **Visual C#/Windows/Windows 8/Aplikacje uniwersalne/centralne**) przejdź do menu **Narzędzia** i kliknij polecenie **Wywołaj TestUniversalProject**, a następnie sprawdź tekst w okienku **dane wyjściowe** . Powinna zostać wyświetlona zawartość podobna do tej:  
  
    ```  
    Found shared project: HubApp.Shared  
    The active platform project: HubApp.Windows  
    Platform projects:  
     * HubApp.Windows  
     * HubApp.WindowsPhone  
    set active project: HubApp.WindowsPhone  
    Walk the active platform project:  
        HubApp.WindowsPhone  
            <HubApp.Shared>  
                App.xaml  
                    App.xaml.cs  
                Assets  
                    DarkGray.png  
                    LightGray.png  
                    MediumGray.png  
                Common  
                    NavigationHelper.cs  
                    ObservableDictionary.cs  
                    RelayCommand.cs  
                    SuspensionManager.cs  
                DataModel  
                    SampleData.json  
                    SampleDataSource.cs  
                HubApp.Shared.projitems  
                Strings  
                    en-US  
                        Resources.resw  
            Assets  
                HubBackground.theme-dark.png  
                HubBackground.theme-light.png  
                Logo.scale-240.png  
                SmallLogo.scale-240.png  
                SplashScreen.scale-240.png  
                Square71x71Logo.scale-240.png  
                StoreLogo.scale-240.png  
                WideLogo.scale-240.png  
            HubPage.xaml  
                HubPage.xaml.cs  
            ItemPage.xaml  
                ItemPage.xaml.cs  
            Package.appxmanifest  
            Properties  
                AssemblyInfo.cs  
            References  
                .NET for Windows Store apps  
                HubApp.Shared  
                Windows Phone 8.1  
            SectionPage.xaml  
                SectionPage.xaml.cs  
    ```  
  
### <a name="detecting-changes-in-platform-projects-and-shared-projects"></a>Wykrywanie zmian w projektach platformy i projektach udostępnionych  
  
1. Zdarzenia hierarchii i projektu umożliwiają wykrywanie zmian w projektach udostępnionych, podobnie jak w przypadku projektów platformy. Jednak elementy projektu w projekcie udostępnionym nie są widoczne, co oznacza, że niektóre zdarzenia nie są uruchamiane po zmianie elementów projektu udostępnionego.  
  
    Należy wziąć pod uwagę sekwencję zdarzeń, gdy zostanie zmieniona nazwa pliku w projekcie:  
  
   1. Nazwa pliku została zmieniona na dysku.  
  
   2. Plik projektu został zaktualizowany tak, aby zawierał nową nazwę pliku.  
  
      Zdarzenia hierarchii (na przykład <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyEvents> ) zazwyczaj śledzą zmiany wyświetlane w interfejsie użytkownika, jak w **Eksplorator rozwiązań**. Zdarzenia hierarchii należy wziąć pod uwagę operację zmiany nazwy pliku, aby składać się z usuwania plików, a następnie dodawania plików. Jednak po zmianie niewidocznych elementów system zdarzeń hierarchii uruchamia <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyEvents.OnItemDeleted%2A> zdarzenie, ale nie <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyEvents.OnItemAdded%2A> zdarzenie. W związku z tym, jeśli zmienisz nazwę pliku w projekcie platformy, będziesz mieć zarówno, <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyEvents.OnItemDeleted%2A> jak i <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyEvents.OnItemAdded%2A> , ale jeśli zmienisz nazwę pliku w projekcie udostępnionym, uzyskasz tylko <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyEvents.OnItemDeleted%2A> .  
  
      Aby śledzić zmiany w elementach projektu, można obsługiwać zdarzenia elementów projektu DTE (Znalezione w programie <xref:EnvDTE.ProjectItemsEventsClass> ). Jednak w przypadku obsługi dużej liczby zdarzeń można uzyskać lepszą wydajność obsługi zdarzeń w programie <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2> . W tym instruktażu przedstawiono tylko zdarzenia hierarchii i zdarzenia DTE. W tej procedurze należy dodać odbiornik zdarzeń do projektu udostępnionego i projektu platformy. Po zmianie nazwy jednego pliku w projekcie udostępnionym i innym pliku w projekcie platformy można zobaczyć zdarzenia, które są generowane dla każdej operacji zmiany nazwy.  
  
      W tej procedurze należy dodać odbiornik zdarzeń do projektu udostępnionego i projektu platformy. Po zmianie nazwy jednego pliku w projekcie udostępnionym i innym pliku w projekcie platformy można zobaczyć zdarzenia, które są generowane dla każdej operacji zmiany nazwy.  
  
2. Dodaj odbiornik zdarzeń. Dodaj nowy plik klasy do projektu i Wywołaj go HierarchyEventListener.cs.  
  
3. Otwórz plik HierarchyEventListener.cs i Dodaj następujące instrukcje using:  
  
   ```csharp  
   using Microsoft.VisualStudio.Shell.Interop;  
   using Microsoft.VisualStudio;  
   using System.IO;  
  
   ```  
  
4. Zaimplementuj `HierarchyEventListener` klasę <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyEvents> :  
  
   ```csharp  
   class HierarchyEventListener : IVsHierarchyEvents  
   { }  
  
   ```  
  
5. Zaimplementuj elementy członkowskie <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyEvents> , jak w poniższym kodzie.  
  
   ```csharp  
   class HierarchyEventListener : IVsHierarchyEvents  
   {  
       private IVsHierarchy hierarchy;  
       IVsOutputWindowPane output;   
  
       internal HierarchyEventListener(IVsHierarchy hierarchy, IVsOutputWindowPane outputWindow) {  
            this.hierarchy = hierarchy;  
            this.output = outputWindow;  
       }  
  
       int IVsHierarchyEvents.OnInvalidateIcon(IntPtr hIcon) {  
           return VSConstants.S_OK;  
       }  
  
       int IVsHierarchyEvents.OnInvalidateItems(uint itemIDParent) {  
           return VSConstants.S_OK;  
       }  
  
       int IVsHierarchyEvents.OnItemAdded(uint itemIDParent, uint itemIDSiblingPrev, uint itemIDAdded) {  
           output.OutputStringThreadSafe("IVsHierarchyEvents.OnItemAdded: " + itemIDAdded + "\n");  
           return VSConstants.S_OK;  
       }  
  
       int IVsHierarchyEvents.OnItemDeleted(uint itemID) {  
           output.OutputStringThreadSafe("IVsHierarchyEvents.OnItemDeleted: " + itemID + "\n");  
           return VSConstants.S_OK;  
       }  
  
       int IVsHierarchyEvents.OnItemsAppended(uint itemIDParent) {  
           output.OutputStringThreadSafe("IVsHierarchyEvents.OnItemsAppended\n");  
           return VSConstants.S_OK;  
       }  
  
       int IVsHierarchyEvents.OnPropertyChanged(uint itemID, int propID, uint flags) {  
           output.OutputStringThreadSafe("IVsHierarchyEvents.OnPropertyChanged: item ID " + itemID + "\n");  
           return VSConstants.S_OK;  
       }  
   }  
  
   ```  
  
6. W tej samej klasie Dodaj kolejną procedurę obsługi zdarzeń dla zdarzenia DTE <xref:EnvDTE.ProjectItemsEventsClass.ItemRenamed> , która występuje zawsze, gdy zostanie zmieniona nazwa elementu projektu.  
  
   ```csharp  
   public void OnItemRenamed(EnvDTE.ProjectItem projItem, string oldName)  
   {  
       output.OutputStringThreadSafe(string.Format("[Event] Renamed {0} to {1} in project {2}\n",  
            oldName, Path.GetFileName(projItem.get_FileNames(1)), projItem.ContainingProject.Name));  
   }  
   ```  
  
7. Utwórz konto dla zdarzeń hierarchii. Musisz zarejestrować się osobno dla każdego śledzonego projektu. Dodaj następujący kod w `ShowMessageBox` , jeden dla projektu udostępnionego, a drugi dla jednego z projektów platformy.  
  
   ```csharp  
   // hook up the event listener for hierarchy events on the shared project  
   HierarchyEventListener listener1 = new HierarchyEventListener(sharedHier, output);  
   uint cookie1;  
   sharedHier.AdviseHierarchyEvents(listener1, out cookie1);  
  
   // hook up the event listener for hierarchy events on the   
   active project  
   HierarchyEventListener listener2 = new HierarchyEventListener(activePlatformHier, output);  
   uint cookie2;  
   activePlatformHier.AdviseHierarchyEvents(listener2, out cookie2);  
   ```  
  
8. Utwórz konto dla zdarzenia elementu projektu DTE <xref:EnvDTE.ProjectItemsEventsClass.ItemRenamed> . Dodaj następujący kod po podłączaniu drugiego odbiornika.  
  
   ```csharp  
   // hook up DTE events for project items  
   Events2 dteEvents = (Events2)dte.Events;  
   dteEvents.ProjectItemsEvents.ItemRenamed += listener1.OnItemRenamed;  
  
   ```  
  
9. Zmodyfikuj element współużytkowany. Nie można modyfikować elementów udostępnionych w projekcie platformy; Zamiast tego należy je zmodyfikować w projekcie udostępnionym, który jest rzeczywistym właścicielem tych elementów. Możesz uzyskać odpowiedni identyfikator elementu w projekcie udostępnionym z <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject.IsDocumentInProject%2A> , nadając mu pełną ścieżkę do udostępnionego elementu. Następnie można zmodyfikować element współużytkowany. Zmiana jest propagowana do projektów platformy.  
  
    > [!IMPORTANT]
    > Należy sprawdzić, czy element projektu jest elementem udostępnionym przed jego zmodyfikowaniem.  
  
     Poniższa Metoda modyfikuje nazwę pliku elementu projektu.  
  
    ```csharp  
    private void ModifyFileNameInProject(IVsHierarchy project, string path)  
    {    
        int found;  
        uint projectItemID;  
        VSDOCUMENTPRIORITY[] priority = new VSDOCUMENTPRIORITY[1];  
        if (ErrorHandler.Succeeded(((IVsProject)project).IsDocumentInProject(path, out found, priority, out projectItemID))  
            && found != 0)  
        {  
            var name = DateTime.Now.Ticks.ToString() + Path.GetExtension(path);  
            project.SetProperty(projectItemID, (int)__VSHPROPID.VSHPROPID_EditLabel, name);  
            output.OutputStringThreadSafe(string.Format("Renamed {0} to {1}\n", path,name));  
        }  
    }  
    ```  
  
10. Wywołaj tę metodę po każdym innym kodzie w programie, `ShowMessageBox` Aby zmodyfikować plik w projekcie udostępnionym. Wstaw ten element po kodzie, który pobiera pełną ścieżkę elementu w projekcie udostępnionym.  
  
    ```csharp  
    // change the file name of an item in a shared project  
    this.InspectHierarchyItems(activePlatformHier, (uint)VSConstants.VSITEMID.Root, 1, sharedItemIds, true, true);  
    ErrorHandler.ThrowOnFailure(((IVsProject)activePlatformHier).GetMkDocument(sharedItemId, out fullPath));   
    output.OutputStringThreadSafe(string.Format("Shared project item ID = {0}, full path = {1}\n", sharedItemId, fullPath));  
    this.ModifyFileNameInProject(sharedHier, fullPath);  
    ```  
  
11. Skompiluj i Uruchom projekt. Utwórz aplikację uniwersalną centrum w języku C# w eksperymentalnym wystąpieniu, przejdź do menu **Narzędzia** i kliknij polecenie **Wywołaj TestUniversalProject**i zaznacz tekst w okienku danych wyjściowych ogólne. Nazwa pierwszego elementu w projekcie udostępnionym (oczekujemy, że plik App. XAML) powinien zostać zmieniony i należy zobaczyć, że <xref:EnvDTE.ProjectItemsEventsClass.ItemRenamed> zdarzenie zostało wyzwolone. W takim przypadku zmiana nazwy pliku App. XAML powoduje, że zmiany nazwy App.xaml.cs również powinny być widoczne cztery zdarzenia (dwa dla każdego projektu platformy). (Zdarzenia DTE nie śledzą elementów w projekcie udostępnionym). Powinny być widoczne dwa <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyEvents.OnItemDeleted%2A> zdarzenia (po jednym dla każdego projektu platformy), ale nie <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyEvents.OnItemAdded%2A> zdarzenia.  
  
12. Teraz spróbuj zmienić nazwę pliku w projekcie platformy i zobaczyć różnicę w zdarzeniach, które są wywoływane. Dodaj następujący kod do programu `ShowMessageBox` po wywołaniu metody `ModifyFileName` .  
  
    ```csharp  
    // change the file name of an item in a platform project  
    var unsharedItemIds = new List<uint>();  
    this.InspectHierarchyItems(activePlatformHier, (uint)VSConstants.VSITEMID.Root, 1, unsharedItemIds, false, false);  
  
    var unsharedItemId = unsharedItemIds[0];  
    string unsharedPath;  
    ErrorHandler.ThrowOnFailure(((IVsProject)activePlatformHier).GetMkDocument(unsharedItemId, out unsharedPath));  
    output.OutputStringThreadSafe(string.Format("Platform project item ID = {0}, full path = {1}\n", unsharedItemId, unsharedPath));  
  
    this.ModifyFileNameInProject(activePlatformHier, unsharedPath);  
    ```  
  
13. Skompiluj i Uruchom projekt. Utwórz projekt uniwersalny C# w eksperymentalnym wystąpieniu, przejdź do menu **Narzędzia** i kliknij polecenie **Wywołaj TestUniversalProject**i zaznacz tekst w okienku danych wyjściowych ogólne. Po zmianie nazwy pliku w projekcie platformy powinno być widoczne <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyEvents.OnItemAdded%2A> zdarzenie i <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyEvents.OnItemDeleted%2A> zdarzenie. Ponieważ zmiana pliku spowodowała, że nie można zmienić plików, a ponieważ zmiany elementów w projekcie platformy nie są propagowane w dowolnym miejscu, istnieje tylko jedno z tych zdarzeń.
