---
title: Weryfikowanie podtypów projektu w czasie wykonywania | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- project subtypes
- check subtypes
ms.assetid: b87780ec-36a3-4e9a-9ee2-7abdc26db739
caps.latest.revision: 12
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 1e3940097ac53255b7bdd2c12c9ccc64605016e1
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "62584908"
---
# <a name="verifying-subtypes-of-a-project-at-run-time"></a>Weryfikowanie podtypów projektu w czasie wykonywania
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Pakietu VSPackage, który zależy od niestandardowego podtypu projektu, powinien zawierać logikę do wyszukania tego podtypu, aby można było bezpiecznie kończyć się niepowodzeniem, jeśli podtyp nie jest obecny. Poniższa procedura pokazuje, jak sprawdzić obecność określonego podtypu.  
  
### <a name="to-verify-the-presence-of-a-subtype"></a>Aby zweryfikować obecność podtypu  
  
1. Uzyskaj hierarchię projektu z obiektów projektu i rozwiązania jako obiekt, <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> dodając następujący kod do pakietu VSPackage.  
  
    ```  
    EnvDTE.DTE dte;  
    dte = (EnvDTE.DTE)Package.GetGlobalService(typeof(EnvDTE.DTE));  
  
    EnvDTE.Project project;  
    project = dte.Solution.Projects.Item(1);  
  
    IVsSolution solution;  
    solution = (IVsSolution)Package.GetGlobalService(typeof(SVsSolution));  
  
    IVsHierarchy hierarchy;  
    hierarchy = solution.GetProjectOfUniqueName(project.UniqueName);  
  
    ```  
  
2. Rzutowanie hierarchii do <xref:Microsoft.VisualStudio.Shell.Flavor.IVsAggregatableProjectCorrected> interfejsu.  
  
    ```  
    IVsAggregatableProjectCorrected AP;  
    AP = hierarchy as IVsAggregatableProjectCorrected;  
  
    ```  
  
3. Pobierz listę identyfikatorów GUID typu projektu, wywołując <xref:Microsoft.VisualStudio.Shell.Flavor.IVsAggregatableProjectCorrected.GetAggregateProjectTypeGuids%2A> .  
  
    ```  
    string projTypeGuids = AP.GetAggregateProjectTypeGuids().ToUpper();  
  
    ```  
  
4. Sprawdź listę identyfikatorów GUID określonego podtypu.  
  
    ```  
    // Replace the string "MyGUID" with the GUID of the subtype.  
    string guidMySubtype = "MyGUID";  
    if (projTypeGuids.IndexOf(guidMySubtype) > 0)  
    {  
        // The specified subtype is present.  
    }  
    ```  
  
## <a name="see-also"></a>Zobacz też  
 [Podtypy projektu](../extensibility/internals/project-subtypes.md)   
 [Projekt podtypów projektu](../extensibility/internals/project-subtypes-design.md)   
 [Właściwości i metody rozszerzane przez podtypy projektów](../extensibility/internals/properties-and-methods-extended-by-project-subtypes.md)
