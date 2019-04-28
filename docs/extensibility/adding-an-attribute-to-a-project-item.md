---
title: Dodawanie atrybutu do elementu projektu | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- attributes [Visual Studio], adding to a project item
ms.assetid: 404a71d5-cce5-44e7-9eaf-d747c794fedb
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: b6992790be2a447c1539024d21d751041d43da2f
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62843917"
---
# <a name="add-an-attribute-to-a-project-item"></a>Dodawanie atrybutu do elementu projektu
Metody <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage.GetItemAttribute%2A> i <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage.SetItemAttribute%2A> pobieranie i ustawianie wartości atrybutów elementu projektu. SetItemAttribute tworzy atrybut, jeśli go jeszcze nie istnieje, dodając go do metadanych elementu projektu.

## <a name="add-an-attribute-to-a-project-item"></a>Dodawanie atrybutu do elementu projektu

- Poniższy kod używa <xref:EnvDTE.DTE> obiektu automatyzacji i <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage.SetItemAttribute%2A> metodę, aby dodać atrybut do elementu projektu. Identyfikator elementu projektu jest uzyskiwany z nazwy elementu projektu "program.cs". Atrybut "MyAttribute" zostanie dodany do tego elementu projektu i danej wartości "MyValue".

    ```csharp
    EnvDTE.DTE dte = (EnvDTE.DTE)Package.GetGlobalService(typeof(EnvDTE.DTE));
    EnvDTE.Project project = dte.Solution.Projects.Item(1);

    string uniqueName = project.UniqueName;
    IVsSolution solution = (IVsSolution)Package.GetGlobalService(typeof(SVsSolution));
    IVsHierarchy hierarchy;
    solution.GetProjectOfUniqueName(uniqueName, out hierarchy);
    IVsBuildPropertyStorage buildPropertyStorage = hierarchy as IVsBuildPropertyStorage;
    if (buildPropertyStorage != null)
    {
        uint itemId;
        string fullPath = (string)project.ProjectItems.Item("Program.cs").Properties.Item("FullPath").Value;
        hierarchy.ParseCanonicalName(fullPath, out itemId);
        buildPropertyStorage.SetItemAttribute(itemId, "MyAttribute", "MyValue");
    }

    ```

## <a name="see-also"></a>Zobacz także
- [Utrwalanie danych w pliku projektu MSBuild](../extensibility/internals/persisting-data-in-the-msbuild-project-file.md)
