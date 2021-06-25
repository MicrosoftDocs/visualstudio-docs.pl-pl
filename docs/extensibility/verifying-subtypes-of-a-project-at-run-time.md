---
title: Weryfikowanie podtypów projektu w czasie | Microsoft Docs
description: Dowiedz się, jak pakiet VSPackage zweryfikować obecność określonego niestandardowego podtypu projektu, od których zależy.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- project subtypes
- check subtypes
ms.assetid: b87780ec-36a3-4e9a-9ee2-7abdc26db739
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 621a40e1857d7c78ec4c5be08a3b7c3808a0d48b
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/25/2021
ms.locfileid: "112905476"
---
# <a name="verify-subtypes-of-a-project-at-run-time"></a>Weryfikowanie podtypów projektu w czasie uruchamiania
Pakiet VSPackage, który jest zależny od niestandardowego podtypu projektu, powinien zawierać logikę wyszukiwania tego podtypu, aby bezpiecznie zakończyło się niepowodzeniem, jeśli podtyp nie istnieje. W poniższej procedurze pokazano, jak sprawdzić obecność określonego podtypu.

### <a name="to-verify-the-presence-of-a-subtype"></a>Aby sprawdzić obecność podtypu

1. Pobierz hierarchię projektu z obiektów projektu i rozwiązania jako obiekt, dodając <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> następujący kod do pakietów VSPackage.

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

2. Rzutuj hierarchię na <xref:Microsoft.VisualStudio.Shell.Flavor.IVsAggregatableProjectCorrected> interfejs.

    ```csharp
    IVsAggregatableProjectCorrected AP;
    AP = hierarchy as IVsAggregatableProjectCorrected;

    ```

3. Pobierz listę identyfikatorów GUID typu projektu przez wywołania <xref:Microsoft.VisualStudio.Shell.Flavor.IVsAggregatableProjectCorrected.GetAggregateProjectTypeGuids%2A> .

    ```csharp
    string projTypeGuids = AP.GetAggregateProjectTypeGuids().ToUpper();

    ```

4. Sprawdź listę identyfikatorów GUID określonego podtypu.

    ```csharp
    // Replace the string "MyGUID" with the GUID of the subtype.
    string guidMySubtype = "MyGUID";
    if (projTypeGuids.IndexOf(guidMySubtype) > 0)
    {
        // The specified subtype is present.
    }
    ```

## <a name="see-also"></a>Zobacz też
- [Podtypy projektu](../extensibility/internals/project-subtypes.md)
- [Projekt podtypów projektu](../extensibility/internals/project-subtypes-design.md)
- [Właściwości i metody rozszerzone o podtypy projektu](../extensibility/internals/properties-and-methods-extended-by-project-subtypes.md)
