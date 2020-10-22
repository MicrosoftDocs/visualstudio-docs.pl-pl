---
title: AssignTargetPath — Zadanie | Microsoft Docs
description: Za pomocą zadania MSBuild AssignTargetPath Zaakceptuj listę plików i Dodaj atrybuty TargetPath, jeśli nie zostały one jeszcze określone.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
ms.assetid: 0e830e31-3bcf-4259-b2a8-a5df49b92d51
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 5e56bb8817551e24d1b5aceef2f571e35f1db43e
ms.sourcegitcommit: d3bca34f82de03fa34ecdd72233676c17fb3cb14
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/22/2020
ms.locfileid: "92353333"
---
# <a name="assigntargetpath-task"></a>AssignTargetPath, zadanie

To zadanie akceptuje listę plików i dodaje atrybuty, `<TargetPath>` Jeśli nie zostały one jeszcze określone.

## <a name="task-parameters"></a>Parametry zadania

W poniższej tabeli opisano parametry `AssignTargetPath` zadania.

|Parametr|Opis|
|---------------|-----------------|
|`RootFolder`|Opcjonalny `string` parametr wejściowy.<br /><br /> Zawiera ścieżkę do folderu, który zawiera linki docelowe.|
|`Files`|Opcjonalny <xref:Microsoft.Build.Framework.ITaskItem> `[]` parametr wejściowy.<br /><br /> Zawiera przychodzącą listę plików.|
|`AssignedFiles`|Opcjonalne<br /><br /> <xref:Microsoft.Build.Framework.ITaskItem>`[]`parametr wyjściowy.<br /><br /> Zawiera uzyskaną listę plików.|

## <a name="remarks"></a>Uwagi

Oprócz parametrów wymienionych powyżej, to zadanie dziedziczy parametry z <xref:Microsoft.Build.Tasks.TaskExtension> klasy, która sama dziedziczy z <xref:Microsoft.Build.Utilities.Task> klasy. Aby zapoznać się z listą tych dodatkowych parametrów i ich opisów, zobacz [TaskExtension Base Class](../msbuild/taskextension-base-class.md).

## <a name="example"></a>Przykład

Poniższy przykład wykonuje zadanie, `AssignTargetPath` Aby skonfigurować projekt.

```xml
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
    <Target Name="MyProject">
        <AssignTargetPath
RootFolder="Resources"
            Files="@(ResourceFiles)"
            <Output TaskParameter="AssignedFiles"
                ItemName="OutAssignedFiles"/>
        </AssignTargetPath>
    </Target>
</Project>
```

## <a name="see-also"></a>Zobacz też

- [Zadania](../msbuild/msbuild-tasks.md)
- [Dokumentacja zadań](../msbuild/msbuild-task-reference.md)
