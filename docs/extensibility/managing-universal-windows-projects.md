---
title: Zarządzanie projektami Windows Universal | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 47926aa1-3b41-410d-bca8-f77fc950cbe7
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 06bfb109ce58ee822a32bc3a92d7e6e45578fb05
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/25/2019
ms.locfileid: "55005513"
---
# <a name="manage-universal-windows-projects"></a>Zarządzaj projektami Universal Windows
Universal Windows apps to aplikacje, przeznaczonych dla Windows 8.1 i Windows Phone 8.1 dzięki czemu deweloperzy mogą używać kodu i inne zasoby w obu platform. Wspólny kod i zasoby są przechowywane w udostępnionego projektu, gdy kod specyficzny dla platform i zasobów, które są przechowywane w oddzielnych projektów: jeden dla Windows, a drugi dla Windows Phone. Aby uzyskać więcej informacji na temat uniwersalnych aplikacji dla Windows, zobacz [Universal Windows apps](https://msdn.microsoft.com/library/windows/apps/dn609832.aspx). Rozszerzenia programu Visual Studio, zarządzanie projektami, które należy pamiętać, że uniwersalne projekty aplikacji Windows mają strukturę, która różni się od aplikacji pojedynczej platformy. W tym instruktażu dowiesz się, jak nawigować udostępnionego projektu i zarządzanie elementami udostępnionymi.  

## <a name="prerequisites"></a>Wymagania wstępne  
 Począwszy od programu Visual Studio 2015, możesz nie należy instalować programu Visual Studio SDK z Centrum pobierania. Jest dołączony jako opcjonalna funkcja w Instalatorze programu Visual Studio. Możesz także zainstalować zestaw SDK programu VS później. Aby uzyskać więcej informacji, zobacz [instalacji programu Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).  

### <a name="navigate-the-shared-project"></a>Przejdź do projektu udostępnionego  

1.  Utwórz projekt VSIX języka C# o nazwie **TestUniversalProject**. (**Pliku** > **nowe** > **projektu** i następnie **C#**  >   **Rozszerzalność** > **pakietu Visual Studio**). Dodaj **polecenia niestandardowego** szablonu elementu projektu (na **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy węzeł projektu i wybierz **Dodaj** > **nowy element** , a następnie przejdź do **rozszerzalności**). Nadaj plikowi nazwę **TestUniversalProject**.  

2.  Dodaj odwołanie do *Microsoft.VisualStudio.Shell.Interop.12.1.DesignTime.dll* i *Microsoft.VisualStudio.Shell.Interop.14.0.DesignTime.dll* (w **rozszerzenia** sekcji).  

3.  Otwórz *TestUniversalProject.cs* i dodaj następującą `using` instrukcji:  

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

4.  W `TestUniversalProject` klasy, Dodaj pole prywatne wskazuje **dane wyjściowe** okna.  

    ```csharp  
    public sealed class TestUniversalProject   
    {  
        IVsOutputWindowPane output;  
    . . .  
    }  
    ```  

5.  Ustaw odwołanie do okienka danych wyjściowych w Konstruktorze TestUniversalProject:  

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

6.  Usuń istniejący kod z `ShowMessageBox` metody:  

    ```csharp  
    private void ShowMessageBox(object sender, EventArgs e)   
    {  
    }  
    ```  

7.  Pobierz obiekt DTE, którego użyto do kilku różnych celów, w tym przewodniku. Ponadto upewnij się, że rozwiązanie jest załadowany po kliknięciu przycisku menu.  

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

8.  Znajdź projektu udostępnionego. Udostępnionego projektu jest kontenerem czysty; Nie twórz ani tworzyć dane wyjściowe. Następującą metodę znajdzie pierwszy udostępnionego projektu w rozwiązaniu, wyszukując <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> obiekt, który ma zdolność projektu udostępnionego.  

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

9. W `ShowMessageBox` metody, dane wyjściowe podpisem (nazwa projektu, który pojawia się w **Eksploratora rozwiązań**) z udostępnionego projektu.  

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

10. Uzyskaj projektów aktywnej platformy. Projekty platformy są projektami, które zawierają kod specyficzny dla platform i zasobów. Poniższa metoda używa nowego pola <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID7> można pobrać projektów aktywnej platformy.  

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

11. W `ShowMessageBox` metody, dane wyjściowe podpisem projektów aktywnej platformy.  

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

12. Wykonaj iterację w projektach platformy. Poniższa metoda pobiera wszystkie importującego projekty (platformy) z udostępnionego projektu.  

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
    >  Jeśli użytkownik został otwarty projekt aplikacji Windows universal C++ w doświadczalnym wystąpieniu, powyższy kod zgłasza wyjątek. Jest to znany problem. Aby uniknąć wyjątek, należy zastąpić `foreach` block powyżej następującym kodem:  

    ```csharp  
    var importingProjects = sharedAssetsProject.EnumImportingProjects();  
    for (int i = 0; i < importingProjects.Count; ++i)  
    {  
        yield return importingProjects[i];  
    }   
    ```  

13. W `ShowMessageBox` metody, dane wyjściowe podpisem każdy projekt platformy. Wstaw następujący kod po wierszu, który wyświetla napis projektów aktywnej platformy. Na tej liście są wyświetlane tylko projekty platformy, które są ładowane.  

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

14. Zmień projektów aktywnej platformy. Następujące metody ustawia aktywny projekt za pomocą <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.SetProperty%2A>.  

    ```csharp  
    private int SetActiveProjectContext(IVsHierarchy hierarchy, IVsHierarchy activeProjectContext)  
    {  
        return hierarchy.SetProperty((uint)VSConstants.VSITEMID.Root, (int)__VSHPROPID7.VSHPROPID_SharedItemContextHierarchy, activeProjectContext);  
    }  
    ```  

15. W `ShowMessageBox` metodę, zmień projektów aktywnej platformy. Wstaw ten kod wewnątrz `foreach` bloku.  

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

16. Teraz wypróbuj działanie rozwiązania. Naciśnij klawisz F5, aby uruchomić doświadczalne wystąpienie. Tworzenie projektu aplikacji uniwersalnej Centrum C# w doświadczalnym wystąpieniu (w **nowy projekt** okno dialogowe **Visual C#** > **Windows**  >   **System Windows 8** > **Universal** > **aplikacja Centrum zawartości**). Po załadowaniu rozwiązania, przejdź do **narzędzia** menu i kliknij przycisk **wywołania TestUniversalProject**, a następnie zaewidencjonuj tekst **dane wyjściowe** okienka. Powinien zostać wyświetlony podobny do poniższego:  

    ```  
    Found shared project: HubApp.Shared  
    The active platform project: HubApp.Windows  
    Platform projects:  
     * HubApp.Windows  
     * HubApp.WindowsPhone  
    set active project: HubApp.WindowsPhone  
    ```  

### <a name="manage-the-shared-items-in-the-platform-project"></a>Zarządzanie udostępnione elementy w projekcie platformy  

1.  Znajdź elementy z udostępnionego projektu platformy. Elementy projektu udostępnionego są wyświetlane w projekcie platformy jako elementów udostępnionych. Nie widzisz ich w **Eksploratora rozwiązań**, ale możesz zapoznać się z hierarchii projektu, aby je znaleźć. Następującą metodę przedstawia hierarchię i zbiera wszystkie udostępnione elementy. Opcjonalnie wyświetla napis każdego elementu. Udostępnione elementy, które są identyfikowane przez nową właściwość <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID7>.  

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

2.  W `ShowMessageBox` metody, Dodaj następujący kod, aby zapoznać się z elementów hierarchii projektu platformy. Wstaw go wewnątrz `foreach` bloku.  

    ```csharp  
    output.OutputStringThreadSafe("Walk the active platform project:\n");  
    var sharedItemIds = new List<uint>();  
    this.InspectHierarchyItems(activePlatformHier, (uint)VSConstants.VSITEMID.Root, 1, sharedItemIds, true, true);  
    ```  

3.  Przeczytaj elementów udostępnionych. Udostępnione elementy, które pojawiają się w projekcie platformy jako ukryte pliki połączone i może odczytywać wszystkie właściwości zwykłych plików połączonych. Poniższy kod odczytuje pełną ścieżkę pierwszego elementu udostępnionych.  

    ```csharp  
    var sharedItemId = sharedItemIds[0];  
    string fullPath;  
    ErrorHandler.ThrowOnFailure(((IVsProject)activePlatformHier).GetMkDocument(sharedItemId, out fullPath));  
    output.OutputStringThreadSafe(string.Format("Shared item full path: {0}\n", fullPath));  
    ```  

4.  Teraz wypróbuj działanie rozwiązania. Naciśnij klawisz **F5** można uruchomić doświadczalne wystąpienie. Tworzenie C# projektu aplikacji uniwersalnej Centrum w doświadczalnym wystąpieniu (w **nowy projekt** okno dialogowe **Visual C#**   >  **Windows**  >  **Systemu Windows 8** > **Universal** > **aplikacja Centrum zawartości**) przejdź do **narzędzia** menu i kliknij przycisk  **Wywoływanie TestUniversalProject**, a następnie zaewidencjonuj tekst **dane wyjściowe** okienka. Powinien zostać wyświetlony podobny do poniższego:  

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

### <a name="detect-changes-in-platform-projects-and-shared-projects"></a>Wykrywanie zmian w projektach platformy i projekty udostępnione  

1. Zdarzenia hierarchii i projektu służy do wykrywania zmian w udostępnionych projektach, tak jak w przypadku projektów platformy. Jednak elementy projektu w projekcie udostępnionym nie są widoczne, co oznacza, że określone zdarzenia nie zostać wywołane podczas elementy projektu udostępnionego są zmieniane.  

    Należy wziąć pod uwagę kolejność zdarzeń przy zmianie ich nazwy pliku w projekcie:  

   1. Nazwa pliku zostanie zmieniona na dysku.  

   2. Plik projektu zostanie zaktualizowany do uwzględnienia nową nazwę pliku.  

      Zdarzenia hierarchii (na przykład <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyEvents>) ogólnie śledzenia zmian wyświetlany w Interfejsie użytkownika, podobnie jak w **Eksploratora rozwiązań**. Zdarzenia w hierarchii należy wziąć pod uwagę operacji zmiany nazwy pliku składającej się ze usunięcie pliku, a następnie dodanie pliku. Jednak po zmianie elementów niewidoczne uruchamia system zdarzeń hierarchii <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyEvents.OnItemDeleted%2A> zdarzenia, ale nie <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyEvents.OnItemAdded%2A> zdarzeń. W związku z tym, jeśli zmienisz nazwę pliku w projekcie platformy, możesz uzyskać zarówno <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyEvents.OnItemDeleted%2A> i <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyEvents.OnItemAdded%2A>, ale w przypadku zmiany nazwy pliku w projekcie udostępnionym, otrzymasz tylko <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyEvents.OnItemDeleted%2A>.  

      Aby śledzić zmiany w elementach projektu, które ułatwią Ci obsługę zdarzenia elementu projektu obiektu DTE (te znalezione w <xref:EnvDTE.ProjectItemsEventsClass>). Jednak jeśli obsługi dużej liczby zdarzeń, możesz ją uzyskać lepszą wydajność obsługi zdarzeń w <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2>. W tym instruktażu przedstawiono tylko zdarzenia hierarchii i zdarzenia DTE. W ramach tej procedury dodasz odbiornik zdarzeń do projektu udostępnionego i projekt platformy. Następnie po zmianie nazwy jeden plik w projekcie udostępnionym i inny plik w projekcie platformy, widać zdarzenia, które są uruchamiane dla każdej operacji zmiany nazwy.  

      W ramach tej procedury dodasz odbiornik zdarzeń do projektu udostępnionego i projekt platformy. Następnie po zmianie nazwy jeden plik w projekcie udostępnionym i inny plik w projekcie platformy, widać zdarzenia, które są uruchamiane dla każdej operacji zmiany nazwy.  

2. Dodaj odbiornik zdarzeń. Dodaj nowy plik klasy do projektu i wywołać go *HierarchyEventListener.cs*.  

3. Otwórz *HierarchyEventListener.cs* pliku i dodaj następujące instrukcje using:  

   ```csharp  
   using Microsoft.VisualStudio.Shell.Interop;  
   using Microsoft.VisualStudio;  
   using System.IO;  

   ```  

4. Masz `HierarchyEventListener` implementacji klasy <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyEvents>:  

   ```csharp  
   class HierarchyEventListener : IVsHierarchyEvents  
   { }  

   ```  

5. Implementowanie członkowie <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyEvents>, jak w poniższym kodzie.  

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

6. W tej samej klasie dodać innego programu obsługi zdarzeń dla zdarzenia DTE <xref:EnvDTE.ProjectItemsEventsClass.ItemRenamed>, która pojawia się w każdym przypadku, gdy element projektu została zmieniona.  

   ```csharp  
   public void OnItemRenamed(EnvDTE.ProjectItem projItem, string oldName)  
   {  
       output.OutputStringThreadSafe(string.Format("[Event] Renamed {0} to {1} in project {2}\n",  
            oldName, Path.GetFileName(projItem.get_FileNames(1)), projItem.ContainingProject.Name));  
   }  
   ```  

7. Zarejestruj się w przypadku zdarzeń hierarchii. Musisz zarejestrować się osobno dla każdego projektu, które są śledzone. Dodaj następujący kod w `ShowMessageBox`, jeden dla projektu udostępnionego, a drugi dla jednego z projektów platformy.  

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

8. Zamów zdarzenie elementu projektu obiektu DTE <xref:EnvDTE.ProjectItemsEventsClass.ItemRenamed>. Dodaj następujący kod po podpiąć drugiego odbiornika.  

   ```csharp  
   // hook up DTE events for project items  
   Events2 dteEvents = (Events2)dte.Events;  
   dteEvents.ProjectItemsEvents.ItemRenamed += listener1.OnItemRenamed;  

   ```  

9. Modyfikowanie udostępnionego elementu. Nie można zmodyfikować udostępnione elementy w projekcie platformy; Zamiast tego należy je zmodyfikować w projekcie udostępnionym, który jest rzeczywista właścicielem tych elementów. Możesz pobrać odpowiedni identyfikator elementu w ramach projektu udostępnionego z <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject.IsDocumentInProject%2A>, nadając mu pełna ścieżka udostępnionego elementu. Następnie można zmodyfikować udostępniony element. Zmiana jest propagowana do projektów platformy.  

    > [!IMPORTANT]
    >  Powinien znajdować się, czy element projektu udostępnionego elementu przed zmodyfikowaniem.  

     Poniższa metoda modyfikuje nazwa pliku elementu projektu.  

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

10. Tę metodę należy wywołać po wszystkich innych kodu w `ShowMessageBox` do zmodyfikowania elementu w projekcie udostępnionym nazwą pliku. Wstaw ten po kodzie, który pobiera pełną ścieżkę elementu projektu udostępnionego.  

    ```csharp  
    // change the file name of an item in a shared project  
    this.InspectHierarchyItems(activePlatformHier, (uint)VSConstants.VSITEMID.Root, 1, sharedItemIds, true, true);  
    ErrorHandler.ThrowOnFailure(((IVsProject)activePlatformHier).GetMkDocument(sharedItemId, out fullPath));   
    output.OutputStringThreadSafe(string.Format("Shared project item ID = {0}, full path = {1}\n", sharedItemId, fullPath));  
    this.ModifyFileNameInProject(sharedHier, fullPath);  
    ```  

11. Skompiluj i uruchom projekt. Tworzenie aplikacji uniwersalnych Centrum C# w doświadczalnym wystąpieniu, przejdź do **narzędzia** menu i kliknij przycisk **wywołania TestUniversalProject**i zaznacz tekst, w okienku danych wyjściowych ogólny. Nazwa pierwszego elementu w projekcie udostępnionym (oczekujemy, że jest on *App.xaml* pliku) powinna zostać zmieniona, i należy sprawdzić, która <xref:EnvDTE.ProjectItemsEventsClass.ItemRenamed> jest wyzwalane zdarzenie. W tym przypadku, ponieważ zmiana nazwy *App.xaml* powoduje, że *App.xaml.cs* także ulec zmianie, powinny zostać wyświetlone cztery zdarzenia, (dwa dla każdego projektu platformy). (Zdarzenia DTE "nie Śledź" elementy projektu udostępnionego.) Powinny zostać wyświetlone dwa <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyEvents.OnItemDeleted%2A> zdarzenia (po jednym dla każdej z platform projektów), ale nie <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyEvents.OnItemAdded%2A> zdarzenia.  

12. Teraz spróbuj, zmiana nazwy pliku w projekcie platformy i można zobaczyć różnicę w zdarzeniach, które Pobierz uruchamiane. Dodaj następujący kod w `ShowMessageBox` po wywołaniu `ModifyFileName`.  

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

13. Skompiluj i uruchom projekt. Utwórz projekt Universal C# w doświadczalnym wystąpieniu, przejdź do **narzędzia** menu i kliknij przycisk **wywołania TestUniversalProject**i zaznacz tekst, w okienku danych wyjściowych ogólny. Po zmianie nazwy pliku w projekcie platformy powinien zostać wyświetlony zarówno <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyEvents.OnItemAdded%2A> zdarzeń i <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyEvents.OnItemDeleted%2A> zdarzeń. Ponieważ zmiana pliku spowodowane żadne inne pliki nie mają być zmienione, a ponieważ zmiany wprowadzone w elementy w projekcie platformy nie uzyskać propagowane w dowolnym miejscu, jest tylko jednej z tych zdarzeń.
