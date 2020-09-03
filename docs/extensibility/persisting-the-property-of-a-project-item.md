---
title: Utrwalanie właściwości elementu projektu | Microsoft Docs
ms.date: 03/22/2018
ms.topic: how-to
helpviewer_keywords:
- properties, adding to a project item
- project items, adding properties
ms.assetid: d7a0f2b0-d427-4d49-9536-54edfb37c0f3
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 224a1e4f5f5d56022ae7c1e0572ca648b9a5aa6b
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "85906194"
---
# <a name="persist-the-property-of-a-project-item"></a>Utrwalanie właściwości elementu projektu
Możesz chcieć zachować Właściwość dodawaną do elementu projektu, na przykład autora pliku źródłowego. Można to zrobić, przechowując właściwość w pliku projektu.

 Pierwszym krokiem, aby zachować właściwość w pliku projektu, jest uzyskanie hierarchii projektu jako <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> interfejsu. Ten interfejs można uzyskać za pomocą automatyzacji lub przy użyciu <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection> . Po uzyskaniu interfejsu można za jego pomocą określić, który element projektu jest aktualnie wybrany. Gdy masz identyfikator elementu projektu, możesz użyć, <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage.SetItemAttribute%2A> Aby dodać właściwość.

 W poniższych procedurach należy zachować Właściwość *VsPkg.cs* `Author` z wartością `Tom` w pliku projektu.

## <a name="to-obtain-the-project-hierarchy-with-the-dte-object"></a>Aby uzyskać hierarchię projektu z obiektem DTE

1. Dodaj następujący kod do pakietu VSPackage:

    ```csharp
    EnvDTE.DTE dte = (EnvDTE.DTE)Package.GetGlobalService(typeof(EnvDTE.DTE));
    EnvDTE.Project project = dte.Solution.Projects.Item(1);

    string uniqueName = project.UniqueName;
    IVsSolution solution = (IVsSolution)Package.GetGlobalService(typeof(SVsSolution));
    IVsHierarchy hierarchy;
    solution.GetProjectOfUniqueName(uniqueName, out hierarchy);
    ```

## <a name="to-persist-the-project-item-property-with-the-dte-object"></a>Aby zachować właściwość elementu projektu z obiektem DTE

1. Dodaj następujący kod do kodu podanych w metodzie w poprzedniej procedurze:

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

## <a name="to-obtain-the-project-hierarchy-using-ivsmonitorselection"></a>Aby uzyskać hierarchię projektu przy użyciu IVsMonitorSelection

1. Dodaj następujący kod do pakietu VSPackage:

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

## <a name="to-persist-the-selected-project-item-property-given-the-project-hierarchy"></a>Aby zachować Właściwość wybranego elementu projektu, z uwzględnieniem hierarchii projektu

1. Dodaj następujący kod do kodu podanych w metodzie w poprzedniej procedurze:

    ```csharp
    IVsBuildPropertyStorage buildPropertyStorage =
        hierarchy as IVsBuildPropertyStorage;
    if (buildPropertyStorage != null)
    {
        buildPropertyStorage.SetItemAttribute(itemId, "Author", "Tom");
    }
    ```

## <a name="to-verify-that-the-property-is-persisted"></a>Aby sprawdzić, czy właściwość jest utrwalona

1. Uruchom [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] , a następnie otwórz lub Utwórz rozwiązanie.

2. Wybierz element projektu VsPkg.cs w **Eksplorator rozwiązań**.

3. Użyj punktu przerwania lub w inny sposób Ustal, czy pakietu VSPackage jest załadowany i czy element SetItemAttribute zostanie uruchomiony.

   > [!NOTE]
   > Możesz załadować pakietu VSPackage w kontekście interfejsu użytkownika <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.SolutionExists_guid> . Aby uzyskać więcej informacji, zobacz [Load pakietów VSPackage](../extensibility/loading-vspackages.md).

4. Zamknij [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] , a następnie otwórz plik projektu w Notatniku. Znacznik powinien zostać wyświetlony \<Author> z wartością Tomasz w następujący sposób:

   ```xml
   <Compile Include="VsPkg.cs">
       <Author>Tom</Author>
   </Compile>
   ```

## <a name="see-also"></a>Zobacz też

- [Narzędzia niestandardowe](../extensibility/internals/custom-tools.md)
