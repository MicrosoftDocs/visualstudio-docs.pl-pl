---
title: Dodawanie atrybutu do elementu projektu | Microsoft Docs
description: Dowiedz się, jak dodać atrybut do elementu projektu w programie Visual Studio przy użyciu metod międzyoperacyjnych Shell getitemattribute i SetItemAttribute.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- attributes [Visual Studio], adding to a project item
ms.assetid: 404a71d5-cce5-44e7-9eaf-d747c794fedb
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 79f96be0d9b2ba661c29cdc1a25d7348bcff6eb1
ms.sourcegitcommit: d6207a3a590c9ea84e3b25981d39933ad5f19ea3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/24/2020
ms.locfileid: "95597915"
---
# <a name="add-an-attribute-to-a-project-item"></a>Dodawanie atrybutu do elementu projektu
Metody <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage.GetItemAttribute%2A> i <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage.SetItemAttribute%2A> pobieranie i ustawianie wartości atrybutów elementu projektu. SetItemAttribute tworzy atrybut, jeśli jeszcze nie istnieje, dodając go do metadanych elementu projektu.

## <a name="add-an-attribute-to-a-project-item"></a>Dodawanie atrybutu do elementu projektu

- Poniższy kod używa <xref:EnvDTE.DTE> obiektu automatyzacji i <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage.SetItemAttribute%2A> metody do dodawania atrybutu do elementu projektu. Identyfikator elementu projektu jest uzyskiwany z nazwy elementu projektu "program.cs". Atrybut "atrybut" jest dodawany do tego elementu projektu i ma wartość "Moja wartość".

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
