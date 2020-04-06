---
title: Utrwalanie właściwości elementu projektu | Dokumenty firmy Microsoft
ms.date: 03/22/2018
ms.topic: conceptual
helpviewer_keywords:
- properties, adding to a project item
- project items, adding properties
ms.assetid: d7a0f2b0-d427-4d49-9536-54edfb37c0f3
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 15c280f15436a5e27bcc0dcc4d2fb9e9bdd82933
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80702211"
---
# <a name="persist-the-property-of-a-project-item"></a>Utrwalanie właściwości elementu projektu
Można utrwalić właściwość dodaną do elementu projektu, na przykład autor pliku źródłowego. Można to zrobić, przechowując właściwość w pliku projektu.

 Pierwszym krokiem do utrwalenia właściwości w pliku projektu jest <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> uzyskanie hierarchii projektu jako interfejsu. Ten interfejs można uzyskać za pomocą automatyzacji lub za pomocą programu <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection>. Po uzyskaniu interfejsu można go użyć do określenia, który element projektu jest aktualnie wybrany. Po uzyskaniu identyfikatora elementu projektu można <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage.SetItemAttribute%2A> użyć do dodania właściwości.

 W poniższych procedurach należy utrwalić `Author` `Tom` *właściwość VsPkg.cs* z wartością w pliku projektu.

## <a name="to-obtain-the-project-hierarchy-with-the-dte-object"></a>Aby uzyskać hierarchię projektu za pomocą obiektu DTE

1. Dodaj następujący kod do vspackage:

    ```csharp
    EnvDTE.DTE dte = (EnvDTE.DTE)Package.GetGlobalService(typeof(EnvDTE.DTE));
    EnvDTE.Project project = dte.Solution.Projects.Item(1);

    string uniqueName = project.UniqueName;
    IVsSolution solution = (IVsSolution)Package.GetGlobalService(typeof(SVsSolution));
    IVsHierarchy hierarchy;
    solution.GetProjectOfUniqueName(uniqueName, out hierarchy);
    ```

## <a name="to-persist-the-project-item-property-with-the-dte-object"></a>Aby utrwalić właściwość elementu projektu z obiektem DTE

1. Dodaj następujący kod do kodu podanego w metodzie w poprzedniej procedurze:

    ```csharp
    IVsBuildPropertyStorage buildPropertyStorage =
        hierarchy as IVsBuildPropertyStorage;
    if (buildPropertyStorage != null)
    {
        uint itemId;
        string fullPath = (string)project.ProjectItems.Item(
            "VsPkg.cs").Properties.Item("FullPath").Value;
        hierarchy.ParseCanonicalName(fullPath, out itemId);
        buildPropertyStorage.SetItemAttribute(itemId, "Author", "Tom");
    }
    ```

## <a name="to-obtain-the-project-hierarchy-using-ivsmonitorselection"></a>Aby uzyskać hierarchię projektu przy użyciu iVsMonitorSelection

1. Dodaj następujący kod do vspackage:

    ```csharp
    IVsHierarchy hierarchy = null;
    IntPtr hierarchyPtr = IntPtr.Zero;
    IntPtr selectionContainer = IntPtr.Zero;
    uint itemid;

    // Retrieve shell interface in order to get current selection
    IVsMonitorSelection monitorSelection =     Package.GetGlobalService(typeof(SVsShellMonitorSelection)) as     IVsMonitorSelection;
    if (monitorSelection == null)
        throw new InvalidOperationException();

    try
    {
        // Get the current project hierarchy, project item, and selection container for the current selection
        // If the selection spans multiple hierachies, hierarchyPtr is Zero
        IVsMultiItemSelect multiItemSelect = null;
        ErrorHandler.ThrowOnFailure(
            monitorSelection.GetCurrentSelection(
                out hierarchyPtr, out itemid,
                out multiItemSelect, out selectionContainer));

        // We only care if there is only one node selected in the tree
        if (!(itemid == VSConstants.VSITEMID_NIL ||
            hierarchyPtr == IntPtr.Zero ||
            multiItemSelect != null ||
            itemid == VSConstants.VSITEMID_SELECTION))
        {
            hierarchy = Marshal.GetObjectForIUnknown(hierarchyPtr)
                as IVsHierarchy;
        }
    }
    finally
    {
        if (hierarchyPtr != IntPtr.Zero)
            Marshal.Release(hierarchyPtr);
        if (selectionContainer != IntPtr.Zero)
            Marshal.Release(selectionContainer);
    }
    ```

## <a name="to-persist-the-selected-project-item-property-given-the-project-hierarchy"></a>Aby utrwalić właściwość wybranego elementu projektu, biorąc pod uwagę hierarchię projektu

1. Dodaj następujący kod do kodu podanego w metodzie w poprzedniej procedurze:

    ```csharp
    IVsBuildPropertyStorage buildPropertyStorage =
        hierarchy as IVsBuildPropertyStorage;
    if (buildPropertyStorage != null)
    {
        buildPropertyStorage.SetItemAttribute(itemId, "Author", "Tom");
    }
    ```

## <a name="to-verify-that-the-property-is-persisted"></a>Aby sprawdzić, czy właściwość jest utrwalona

1. Uruchom, [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] a następnie otwórz lub utwórz rozwiązanie.

2. Wybierz element projektu VsPkg.cs w **Eksploratorze rozwiązań**.

3. Użyj punktu przerwania lub w inny sposób ustalić, że vsPackage jest ładowany i że SetItemAttribute działa.

   > [!NOTE]
   > Można automatycznie załadować VSPackage w <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.SolutionExists_guid>kontekście interfejsu użytkownika . Aby uzyskać więcej informacji, zobacz [Ładowanie pakietów VSPackages](../extensibility/loading-vspackages.md).

4. Zamknij, [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] a następnie otwórz plik projektu w Notatniku. Powinien zostać \<wyświetlony tag> autora o wartości Tom, w następujący sposób:

   ```xml
   <Compile Include="VsPkg.cs">
       <Author>Tom</Author>
   </Compile>
   ```

## <a name="see-also"></a>Zobacz też

- [Narzędzia niestandardowe](../extensibility/internals/custom-tools.md)
