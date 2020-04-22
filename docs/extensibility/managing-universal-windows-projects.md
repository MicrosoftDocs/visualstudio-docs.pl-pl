---
title: Zarządzanie uniwersalnymi projektami systemu Windows | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 47926aa1-3b41-410d-bca8-f77fc950cbe7
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: dc6894bcfe3bfab3b0246d716b0bd85152ad17e2
ms.sourcegitcommit: 5c804c42d24d35dcf2ba195aba9ce07031743f62
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2020
ms.locfileid: "81744937"
---
# <a name="manage-universal-windows-projects"></a>Zarządzanie projektami systemu Uniwersalnego systemu Windows

Uniwersalne aplikacje systemu Windows to aplikacje przeznaczone zarówno dla systemu Windows 8.1, jak i Windows Phone 8.1, umożliwiające deweloperom korzystanie z kodu i innych zasobów na obu platformach. Udostępniony kod i zasoby są przechowywane w projekcie udostępnionym, podczas gdy kod i zasoby specyficzne dla platformy są przechowywane w oddzielnych projektach, jeden dla systemu Windows, a drugi dla systemu Windows Phone. Aby uzyskać więcej informacji na temat uniwersalnych aplikacji systemu Windows, zobacz [Uniwersalne aplikacje systemu Windows](https://msdn.microsoft.com/library/windows/apps/dn609832.aspx). Rozszerzenia programu Visual Studio, które zarządzają projektami, powinny mieć świadomość, że uniwersalne projekty aplikacji systemu Windows mają strukturę, która różni się od aplikacji jednoplatformowych. W tym przewodniku pokazano, jak poruszać się po projekcie udostępnionym i zarządzać elementami udostępnionymi.

## <a name="prerequisites"></a>Wymagania wstępne

Począwszy od programu Visual Studio 2015, nie należy instalować visual studio SDK z centrum pobierania. Jest on dołączony jako opcjonalna funkcja w konfiguracji programu Visual Studio. Można również zainstalować vs SDK później. Aby uzyskać więcej informacji, zobacz [Instalowanie pakietu SDK programu Visual Studio](../extensibility/installing-the-visual-studio-sdk.md).

### <a name="navigate-the-shared-project"></a>Poruszanie się po projekcie udostępnionym

1. Utwórz projekt VSIX w języku C# o nazwie **TestUniversalProject**. (Plik**File** > **nowy** > **projekt,** a następnie **C#** > **Rozszerzalność** > pakietu programu Visual**Studio**). Dodaj szablon elementu projektu **polecenia niestandardowego** (w **Eksploratorze rozwiązań**kliknij prawym przyciskiem myszy węzeł projektu i wybierz polecenie **Dodaj** > **nowy element,** a następnie przejdź do **pozycji Rozszerzalność).** Nazwij plik **TestUniversalProject**.

2. Dodaj odwołanie do *pliku Microsoft.VisualStudio.Shell.Interop.12.1.DesignTime.dll* i *Microsoft.VisualStudio.Shell.Interop.14.0.DesignTime.dll* (w sekcji **Rozszerzenia).**

3. Otwórz *TestUniversalProject.cs* i dodaj następujące `using` dyrektywy:

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

4. W `TestUniversalProject` klasie dodać pole prywatne wskazujące na **dane wyjściowe** okna.

    ```csharp
    public sealed class TestUniversalProject
    {
        IVsOutputWindowPane output;
    . . .
    }
    ```

5. Ustaw odwołanie do okienka wyjściowego wewnątrz konstruktora TestUniversalProject:

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

6. Usuń istniejący kod `ShowMessageBox` z metody:

    ```csharp
    private void ShowMessageBox(object sender, EventArgs e)
    {
    }
    ```

7. Pobierz DTE obiektu, który będziemy używać do kilku różnych celów w tym instruktażu. Upewnij się również, że rozwiązanie jest ładowane po kliknięciu przycisku menu.

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

8. Znajdź udostępniony projekt. Wspólny projekt jest czystym kontenerem; nie tworzy ani nie generuje wyników. Poniższa metoda znajduje pierwszy projekt udostępniony w <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> rozwiązaniu, szukając obiektu, który ma możliwości projektu udostępnionego.

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

9. W `ShowMessageBox` metodzie dane wyjściowe podpis (nazwa projektu, który pojawia się w **Eksploratorze rozwiązań)** udostępnionego projektu.

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

10. Pobierz aktywny projekt platformy. Projekty platformy są projekty, które zawierają kod specyficzne dla platformy i zasobów. Poniższa metoda używa nowego <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID7.VSHPROPID_SharedItemContextHierarchy> pola, aby uzyskać projekt aktywnej platformy.

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

11. W `ShowMessageBox` metodzie danych wyjściowych podpis projektu aktywnej platformy.

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
            }
        }
        else
        {
            MessageBox.Show("No solution is open");
        }
    }
    ```

12. Iterować poprzez projekty platformy. Następująca metoda pobiera wszystkie projekty importowania (platformy) z udostępnionego projektu.

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
    > Jeśli użytkownik otworzył projekt aplikacji uniwersalnej systemu Windows języka C++ w wystąpieniu eksperymentalnym, powyższy kod zgłasza wyjątek. Jest to znany problem. Aby uniknąć wyjątku, `foreach` należy zastąpić powyższy blok następującymi elementami:

    ```csharp
    var importingProjects = sharedAssetsProject.EnumImportingProjects();
    for (int i = 0; i < importingProjects.Count; ++i)
    {
        yield return importingProjects[i];
    }
    ```

13. W `ShowMessageBox` metodzie danych wyjściowych podpis każdego projektu platformy. Wstaw następujący kod po wierszu, który wyprowadza podpis projektu aktywnej platformy. Tylko projekty platformy, które są ładowane są wyświetlane na tej liście.

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

14. Zmień projekt aktywnej platformy. Poniższa metoda ustawia aktywny <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.SetProperty%2A>projekt za pomocą .

    ```csharp
    private int SetActiveProjectContext(IVsHierarchy hierarchy, IVsHierarchy activeProjectContext)
    {
        return hierarchy.SetProperty((uint)VSConstants.VSITEMID.Root, (int)__VSHPROPID7.VSHPROPID_SharedItemContextHierarchy, activeProjectContext);
    }
    ```

15. W `ShowMessageBox` metodzie zmień projekt aktywnej platformy. Wstaw ten `foreach` kod wewnątrz bloku.

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

16. Teraz wypróbuj. Naciśnij klawisz F5, aby uruchomić wystąpienie eksperymentalne. Utwórz projekt uniwersalnej aplikacji centrum języka C# w wystąpieniu eksperymentalnym (w oknie dialogowym **Nowy projekt** **aplikacja Visual C#** > **Windows** > **8** > **Universal** > Hub **).** Po załadowaniu rozwiązania przejdź do menu **Narzędzia** i kliknij przycisk **Wywołaj TestUniversalProject**, a następnie sprawdź tekst w okienku **Dane wyjściowe.** Powinna zostać wyświetlona zawartość podobna do tej:

    ```
    Found shared project: HubApp.Shared
    The active platform project: HubApp.Windows
    Platform projects:
     * HubApp.Windows
     * HubApp.WindowsPhone
    set active project: HubApp.WindowsPhone
    ```

### <a name="manage-the-shared-items-in-the-platform-project"></a>Zarządzanie udostępnionymi elementami w projekcie platformy

1. Znajdź elementy udostępnione w projekcie platformy. Elementy w projekcie udostępnionym są wyświetlane w projekcie platformy jako elementy udostępnione. Nie widać ich w **Eksploratorze rozwiązań,** ale można przejść do hierarchii projektu, aby je znaleźć. Poniższa metoda przechodzi hierarchii i zbiera wszystkie elementy udostępnione. Opcjonalnie wyprowadza podpis każdego elementu.It optionally outputs the caption of each item,. Elementy udostępnione są identyfikowane <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID7.VSHPROPID_IsSharedItem>przez nową właściwość .

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

2. W `ShowMessageBox` metodzie dodaj następujący kod, aby przejść do elementów hierarchii projektu platformy. Włóż go `foreach` do bloku.

    ```csharp
    output.OutputStringThreadSafe("Walk the active platform project:\n");
    var sharedItemIds = new List<uint>();
    this.InspectHierarchyItems(activePlatformHier, (uint)VSConstants.VSITEMID.Root, 1, sharedItemIds, true, true);
    ```

3. Przeczytaj udostępnione elementy. Udostępnione elementy są wyświetlane w projekcie platformy jako ukryte połączone pliki i można odczytać wszystkie właściwości jako zwykłe połączone pliki. Poniższy kod odczytuje pełną ścieżkę pierwszego elementu udostępnionego.

    ```csharp
    var sharedItemId = sharedItemIds[0];
    string fullPath;
    ErrorHandler.ThrowOnFailure(((IVsProject)activePlatformHier).GetMkDocument(sharedItemId, out fullPath));
    output.OutputStringThreadSafe(string.Format("Shared item full path: {0}\n", fullPath));
    ```

4. Teraz wypróbuj. Naciśnij **klawisz F5,** aby uruchomić wystąpienie eksperymentalne. Utwórz projekt uniwersalnej aplikacji centrum języka C# w wystąpieniu eksperymentalnym (w oknie dialogowym **Nowy projekt,** **Visual C#** > **Windows** > **8** > **Universal** > Hub**App**) przejdź do menu **Narzędzia** i kliknij przycisk **Wywołaj TestUniversalProject**, a następnie sprawdź tekst w okienku Dane **wyjściowe.** Powinna zostać wyświetlona zawartość podobna do tej:

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

### <a name="detect-changes-in-platform-projects-and-shared-projects"></a>Wykrywanie zmian w projektach platformy i projektach współdzielonych

1. Za pomocą hierarchii i zdarzeń projektu można wykrywać zmiany w projektach udostępnionych, tak samo jak w przypadku projektów platformy. Jednak elementy projektu w projekcie udostępnionym nie są widoczne, co oznacza, że niektóre zdarzenia nie są uruchamiane po zmianie elementów projektu udostępnionego.

    Należy wziąć pod uwagę kolejność zdarzeń, gdy nazwa pliku w projekcie jest zmieniana:

   1. Nazwa pliku zostanie zmieniona na dysku.

   2. Plik projektu zostanie zaktualizowany w celu uwzględnienia nowej nazwy pliku.

      Zdarzenia hierarchii (na <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyEvents>przykład) zazwyczaj śledzą zmiany wyświetlane w interfejsie użytkownika, tak jak w **Eksploratorze rozwiązań**. Zdarzenia hierarchii uważają, że operacja zmiany nazwy pliku składa się z usunięcia pliku, a następnie dodania pliku. Jednak po zmianie niewidocznych elementów system <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyEvents.OnItemDeleted%2A> zdarzeń hierarchii <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyEvents.OnItemAdded%2A> uruchamia zdarzenie, ale nie zdarzenie. W związku z tym jeśli zmienisz nazwę pliku <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyEvents.OnItemDeleted%2A> w <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyEvents.OnItemAdded%2A>projekcie platformy, otrzymasz oba i , ale <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyEvents.OnItemDeleted%2A>jeśli zmienisz nazwę pliku w projekcie udostępnionym, otrzymasz tylko .

      Aby śledzić zmiany w elementach projektu, można obsługiwać <xref:EnvDTE.ProjectItemsEventsClass>zdarzenia elementu projektu DTE (te znalezione w ). Jeśli jednak obsługujesz dużą liczbę zdarzeń, możesz uzyskać lepszą wydajność <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2>obsługi zdarzeń w pliku . W tym instruktażu pokazujemy tylko zdarzenia hierarchii i zdarzenia DTE. W tej procedurze można dodać detektor zdarzeń do udostępnionego projektu i projektu platformy. Następnie po zmianie nazwy jednego pliku w projekcie udostępnionym i innego pliku w projekcie platformy, można zobaczyć zdarzenia, które są uruchamiane dla każdej operacji zmiany nazwy.

      W tej procedurze można dodać detektor zdarzeń do udostępnionego projektu i projektu platformy. Następnie po zmianie nazwy jednego pliku w projekcie udostępnionym i innego pliku w projekcie platformy, można zobaczyć zdarzenia, które są uruchamiane dla każdej operacji zmiany nazwy.

2. Dodaj detektor zdarzeń. Dodaj nowy plik klasy do projektu i nazwij go *HierarchyEventListener.cs*.

3. Otwórz plik *HierarchyEventListener.cs* i dodaj następujące elementy za pomocą dyrektyw:

   ```csharp
   using Microsoft.VisualStudio.Shell.Interop;
   using Microsoft.VisualStudio;
   using System.IO;
   ```

4. Zaimplementuj `HierarchyEventListener` klasę: <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyEvents>

   ```csharp
   class HierarchyEventListener : IVsHierarchyEvents
   { }
   ```

5. Zaimplementuj <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyEvents>członków , jak w poniższym kodzie.

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

6. W tej samej klasie dodać inny <xref:EnvDTE.ProjectItemsEventsClass.ItemRenamed>program obsługi zdarzeń dla zdarzenia DTE , który występuje za każdym razem, gdy element projektu zostanie zmieniona.

   ```csharp
   public void OnItemRenamed(EnvDTE.ProjectItem projItem, string oldName)
   {
       output.OutputStringThreadSafe(string.Format("[Event] Renamed {0} to {1} in project {2}\n",
            oldName, Path.GetFileName(projItem.get_FileNames(1)), projItem.ContainingProject.Name));
   }
   ```

7. Zarejestruj się, aby zarejestrować się w przypadku zdarzeń hierarchii. Musisz zarejestrować się oddzielnie dla każdego projektu, który śledzisz. Dodaj następujący kod `ShowMessageBox`w programie , jeden dla udostępnionego projektu, a drugi dla jednego z projektów platformy.

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

8. Zarejestruj się, aby zarejestrować <xref:EnvDTE.ProjectItemsEventsClass.ItemRenamed>zdarzenie elementu projektu DTE . Dodaj następujący kod po podłączeniu drugiego odbiornika.

   ```csharp
   // hook up DTE events for project items
   Events2 dteEvents = (Events2)dte.Events;
   dteEvents.ProjectItemsEvents.ItemRenamed += listener1.OnItemRenamed;
   ```

9. Modyfikowanie elementu udostępnionego. Nie można modyfikować elementów udostępnionych w projekcie platformy; Zamiast tego należy zmodyfikować je w projekcie udostępnionym, który jest rzeczywistym właścicielem tych elementów. Odpowiedni identyfikator elementu w projekcie udostępnionym <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject.IsDocumentInProject%2A>można uzyskać, nadając mu pełną ścieżkę elementu udostępnionego. Następnie można zmodyfikować element udostępniony. Zmiana jest propagowana do projektów platformy.

    > [!IMPORTANT]
    > Przed zmodyfikowaniem elementu projektu należy dowiedzieć się, czy element projektu jest elementem udostępnionym.

     Poniższa metoda modyfikuje nazwę pliku elementu projektu.

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

10. Wywołanie tej metody po `ShowMessageBox` wszystkich innych kodu w celu zmodyfikowania nazwy pliku elementu w projekcie udostępnionym. Wstaw to po kodzie, który pobiera pełną ścieżkę elementu w projekcie udostępnionym.

    ```csharp
    // change the file name of an item in a shared project
    this.InspectHierarchyItems(activePlatformHier, (uint)VSConstants.VSITEMID.Root, 1, sharedItemIds, true, true);
    ErrorHandler.ThrowOnFailure(((IVsProject)activePlatformHier).GetMkDocument(sharedItemId, out fullPath));
    output.OutputStringThreadSafe(string.Format("Shared project item ID = {0}, full path = {1}\n", sharedItemId, fullPath));
    this.ModifyFileNameInProject(sharedHier, fullPath);
    ```

11. Tworzenie i uruchamianie projektu. Utwórz uniwersalną aplikację centrum języka C# w wystąpieniu eksperymentalnym, przejdź do menu **Narzędzia** i kliknij przycisk **Wywołaj TestUniversalProject**i sprawdź tekst w ogólnym okienku danych wyjściowych. Nazwa pierwszego elementu w projekcie udostępnionym (oczekujemy, że będzie to plik *App.xaml)* powinna <xref:EnvDTE.ProjectItemsEventsClass.ItemRenamed> zostać zmieniona i powinien zostać wyświetlony, że zdarzenie zostało zwolnione. W takim przypadku od zmiany nazwy *App.xaml* *powoduje, App.xaml.cs,* aby zmienić nazwę, jak również, powinny być widoczne cztery zdarzenia (dwa dla każdego projektu platformy). (Zdarzenia DTE nie śledzą elementów w projekcie udostępnionym). Powinny być <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyEvents.OnItemDeleted%2A> widoczne dwa zdarzenia (po jednym <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyEvents.OnItemAdded%2A> dla każdego z projektów platformy), ale bez zdarzeń.

12. Teraz spróbuj zmienić nazwę pliku w projekcie platformy, a zobaczysz różnicę w zdarzeniach, które są uruchamiane. Dodaj następujący kod `ShowMessageBox` po wywołaniu do `ModifyFileName`.

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

13. Tworzenie i uruchamianie projektu. Utwórz projekt uniwersalny języka C# w wystąpieniu eksperymentalnym, przejdź do menu **Narzędzia** i kliknij przycisk **Wywołaj TestUniversalProject**i sprawdź tekst w ogólnym okienku danych wyjściowych. Po zmianie nazwy pliku w projekcie platformy powinien <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyEvents.OnItemAdded%2A> zostać wyświetlony <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyEvents.OnItemDeleted%2A> zarówno zdarzenie, jak i zdarzenie. Ponieważ zmiana pliku spowodowała, że żadne inne pliki nie zostały zmienione, a ponieważ zmiany elementów w projekcie platformy nie są propagowane nigdzie, istnieje tylko jedno z tych zdarzeń.
