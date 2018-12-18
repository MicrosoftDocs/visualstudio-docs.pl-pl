---
title: Weryfikowanie podtypów projektu w czasie wykonywania | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- project subtypes
- check subtypes
ms.assetid: b87780ec-36a3-4e9a-9ee2-7abdc26db739
caps.latest.revision: 12
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 892ba25ff70f62f77016bea1b88436c4f5a6a5b0
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/16/2018
ms.locfileid: "51779895"
---
# <a name="verifying-subtypes-of-a-project-at-run-time"></a>Weryfikowanie podtypów projektu w czasie wykonywania
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Pakietu VSPackage, który jest zależny od podtypu niestandardowego projektu powinna zawierać logikę do wyszukiwania, która podtypu tak, aby go może zakończyć się niepowodzeniem bez problemu zmieniała Jeśli podtyp nie jest obecny. Poniższa procedura pokazuje, jak sprawdzić, czy z określonym podtypem.  
  
### <a name="to-verify-the-presence-of-a-subtype"></a>Aby sprawdzić obecność podtypem  
  
1.  Uzyskaj hierarchii projektu z projektu i rozwiązania obiektów jako <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> obiektu, dodając następujący kod do Twojego pakietu VSPackage.  
  
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
  
2.  Rzutowanie hierarchii, aby <xref:Microsoft.VisualStudio.Shell.Flavor.IVsAggregatableProjectCorrected> interfejsu.  
  
    ```  
    IVsAggregatableProjectCorrected AP;  
    AP = hierarchy as IVsAggregatableProjectCorrected;  
  
    ```  
  
3.  Pobierz listę identyfikatorów GUID. typ projektu, wywołując <xref:Microsoft.VisualStudio.Shell.Flavor.IVsAggregatableProjectCorrected.GetAggregateProjectTypeGuids%2A>.  
  
    ```  
    string projTypeGuids = AP.GetAggregateProjectTypeGuids().ToUpper();  
  
    ```  
  
4.  Sprawdź listę dla identyfikatora GUID z określonym podtypem.  
  
    ```  
    // Replace the string "MyGUID" with the GUID of the subtype.  
    string guidMySubtype = "MyGUID";  
    if (projTypeGuids.IndexOf(guidMySubtype) > 0)  
    {  
        // The specified subtype is present.  
    }  
    ```  
  
## <a name="see-also"></a>Zobacz też  
 [Podtypy projektów](../extensibility/internals/project-subtypes.md)   
 [Projektowanie podtypów projektów](../extensibility/internals/project-subtypes-design.md)   
 [Właściwości i metody rozszerzane przez podtypy projektów](../extensibility/internals/properties-and-methods-extended-by-project-subtypes.md)

