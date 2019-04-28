---
title: Weryfikowanie podtypów projektu w czasie wykonywania | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- project subtypes
- check subtypes
ms.assetid: b87780ec-36a3-4e9a-9ee2-7abdc26db739
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 6ec71ce9be704566640a90c9187abe77f5cc3fe3
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62553991"
---
# <a name="verify-subtypes-of-a-project-at-run-time"></a>Sprawdź podtypów projektu w czasie wykonywania
Pakietu VSPackage, który jest zależny od podtypu niestandardowego projektu powinna zawierać logikę do wyszukiwania, która podtypu tak, aby go może zakończyć się niepowodzeniem bez problemu zmieniała Jeśli podtyp nie jest obecny. Poniższa procedura pokazuje, jak sprawdzić, czy z określonym podtypem.

### <a name="to-verify-the-presence-of-a-subtype"></a>Aby sprawdzić obecność podtypem

1. Pobrać hierarchii projektu z projektu i rozwiązania obiektów jako <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> obiektu, dodając następujący kod do Twojego pakietu VSPackage.

    ```csharp
    EnvDTE.DTE dte;
    dte = (EnvDTE.DTE)Package.GetGlobalService(typeof(EnvDTE.DTE));

    EnvDTE.Project project;
    project = dte.Solution.Projects.Item(1);

    IVsSolution solution;
    solution = (IVsSolution)Package.GetGlobalService(typeof(SVsSolution));

    IVsHierarchy hierarchy;
    hierarchy = solution.GetProjectOfUniqueName(project.UniqueName);

    ```

2. Rzutowanie hierarchii, aby <xref:Microsoft.VisualStudio.Shell.Flavor.IVsAggregatableProjectCorrected> interfejsu.

    ```csharp
    IVsAggregatableProjectCorrected AP;
    AP = hierarchy as IVsAggregatableProjectCorrected;

    ```

3. Pobierz listę identyfikatorów GUID. typ projektu, wywołując <xref:Microsoft.VisualStudio.Shell.Flavor.IVsAggregatableProjectCorrected.GetAggregateProjectTypeGuids%2A>.

    ```csharp
    string projTypeGuids = AP.GetAggregateProjectTypeGuids().ToUpper();

    ```

4. Sprawdź listę dla identyfikatora GUID z określonym podtypem.

    ```csharp
    // Replace the string "MyGUID" with the GUID of the subtype.
    string guidMySubtype = "MyGUID";
    if (projTypeGuids.IndexOf(guidMySubtype) > 0)
    {
        // The specified subtype is present.
    }
    ```

## <a name="see-also"></a>Zobacz także
- [Podtypy projektów](../extensibility/internals/project-subtypes.md)
- [Projektowanie podtypów projektów](../extensibility/internals/project-subtypes-design.md)
- [Właściwości i metody rozszerzane przez podtypy projektów](../extensibility/internals/properties-and-methods-extended-by-project-subtypes.md)