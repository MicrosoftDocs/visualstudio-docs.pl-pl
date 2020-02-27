---
title: AssignTargetPath — Zadanie | Microsoft Docs
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
ms.openlocfilehash: e2d825c0c08ffeba1449954ed310644dd4437840
ms.sourcegitcommit: 96737c54162f5fd5c97adef9b2d86ccc660b2135
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/26/2020
ms.locfileid: "77634542"
---
# <a name="assigntargetpath-task"></a>AssignTargetPath, zadanie

To zadanie akceptuje listę plików i dodaje atrybuty `<TargetPath>`, jeśli nie zostały one jeszcze określone.

## <a name="task-parameters"></a>Parametry zadania

W poniższej tabeli opisano parametry zadania `AssignTargetPath`.

|Parametr|Opis|
|---------------|-----------------|
|`RootFolder`|Opcjonalny `string` parametr wejściowy.<br /><br /> Zawiera ścieżkę do folderu, który zawiera linki docelowe.|
|`Files`|Opcjonalny <xref:Microsoft.Build.Framework.ITaskItem>`[]` parametr wejściowy.<br /><br /> Zawiera przychodzącą listę plików.|
|`AssignedFiles`|Optional (Opcjonalność)<br /><br /> <xref:Microsoft.Build.Framework.ITaskItem> `[]` parametr wyjściowy.<br /><br /> Zawiera uzyskaną listę plików.|

## <a name="remarks"></a>Uwagi

Oprócz parametrów wymienionych powyżej, to zadanie dziedziczy parametry z klasy <xref:Microsoft.Build.Tasks.TaskExtension>, która sama dziedziczy z klasy <xref:Microsoft.Build.Utilities.Task>. Aby zapoznać się z listą tych dodatkowych parametrów i ich opisów, zobacz [TaskExtension Base Class](../msbuild/taskextension-base-class.md).

## <a name="example"></a>Przykład

Poniższy przykład wykonuje zadanie `AssignTargetPath`, aby skonfigurować projekt.

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
- [Odwołanie do zadania](../msbuild/msbuild-task-reference.md)
