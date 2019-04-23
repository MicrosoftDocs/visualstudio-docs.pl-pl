---
title: Utrwalanie właściwości elementu projektu | Dokumentacja firmy Microsoft
ms.date: 03/22/2018
ms.topic: conceptual
helpviewer_keywords:
- properties, adding to a project item
- project items, adding properties
ms.assetid: d7a0f2b0-d427-4d49-9536-54edfb37c0f3
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 58b2495adf66f6c83bc631650e2a0f06f5b7cdd0
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2019
ms.locfileid: "60047388"
---
# <a name="persist-the-property-of-a-project-item"></a>Utrwalanie właściwości elementu projektu
Można utrwalić właściwości dodawane do elementu projektu, takich jak tworzenie pliku źródłowego. Można to zrobić, umieszczając właściwość w pliku projektu.

 Pierwszym krokiem do utrwalenia właściwości w pliku projektu jest uzyskanie hierarchii projektu jako <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> interfejsu. Możesz uzyskać ten interfejs, za pomocą automatyzacji lub za pomocą <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection>. Po uzyskaniu interfejsu, służy do określenia, który element projektu jest aktualnie wybrany. Gdy masz identyfikator elementu projektu, możesz użyć <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage.SetItemAttribute%2A> można dodać właściwości.

 W poniższych procedurach utrwalić *VsPkg.cs* właściwość `Author` wartością `Tom` w pliku projektu.

## <a name="to-obtain-the-project-hierarchy-with-the-dte-object"></a>Aby uzyskać hierarchii projektu obiektu DTE

1. Dodaj następujący kod do Twojego pakietu VSPackage:

    ```csharp
    EnvDTE.DTE dte = (EnvDTE.DTE)Package.GetGlobalService(typeof(EnvDTE.DTE));
    EnvDTE.Project project = dte.Solution.Projects.Item(1);

    string uniqueName = project.UniqueName;
    IVsSolution solution = (IVsSolution)Package.GetGlobalService(typeof(SVsSolution));
    IVsHierarchy hierarchy;
    solution.GetProjectOfUniqueName(uniqueName, out hierarchy);
    ```

## <a name="to-persist-the-project-item-property-with-the-dte-object"></a>Aby zachować właściwości elementu projektu obiektu DTE

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

## <a name="to-obtain-the-project-hierarchy-using-ivsmonitorselection"></a>Aby uzyskać hierarchii projektu przy użyciu IVsMonitorSelection

1. Dodaj następujący kod do Twojego pakietu VSPackage:

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

## <a name="to-persist-the-selected-project-item-property-given-the-project-hierarchy"></a>Można utrwalić właściwość elementu wybranego projektu, biorąc pod uwagę hierarchii projektu

1. Dodaj następujący kod do kodu podanego w metodzie w poprzedniej procedurze:

    ```csharp
    IVsBuildPropertyStorage buildPropertyStorage =
        hierarchy as IVsBuildPropertyStorage;
    if (buildPropertyStorage != null)
    {
        buildPropertyStorage.SetItemAttribute(itemId, "Author", "Tom");
    }
    ```

## <a name="to-verify-that-the-property-is-persisted"></a>Aby sprawdzić, czy właściwość jest trwały.

1. Rozpocznij [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] i otworzyć lub utworzyć rozwiązanie.

2. Wybierz projekt elementu VsPkg.cs w **Eksploratora rozwiązań**.

3. Użyj punktu przerwania lub w przeciwnym razie określenia załadowaniu Twojego pakietu VSPackage i że SetItemAttribute działa.

   > [!NOTE]
   > Można automatycznie załadować pakietu VSPackage w kontekście interfejsu użytkownika <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.SolutionExists_guid>. Aby uzyskać więcej informacji, zobacz [ładowanie pakietów VSPackage](../extensibility/loading-vspackages.md).

4. Zamknij [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] a następnie otwórz plik projektu w programie Notatnik. Powinien zostać wyświetlony \<autor > tag z wartością Tomasz, w następujący sposób:

   ```xml
   <Compile Include="VsPkg.cs">
       <Author>Tom</Author>
   </Compile>
   ```

## <a name="see-also"></a>Zobacz także

- [Narzędzia niestandardowe](../extensibility/internals/custom-tools.md)