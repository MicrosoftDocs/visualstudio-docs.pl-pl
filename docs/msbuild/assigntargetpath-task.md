---
title: AssignTargetPath, zadanie | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
ms.assetid: 0e830e31-3bcf-4259-b2a8-a5df49b92d51
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 21678dd573030076d7248dfb7bbf47ea412cecae
ms.sourcegitcommit: 01334abf36d7e0774329050d34b3a819979c95a2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/07/2019
ms.locfileid: "55853459"
---
# <a name="assigntargetpath-task"></a>Assigntargetpath — zadanie
To zadanie akceptuje listę plików i dodaje `<TargetPath>` atrybuty, jeśli nie są już określone.

## <a name="task-parameters"></a>Parametry zadania
W poniższej tabeli opisano parametry `AssignTargetPath` zadania.

|Parametr|Opis|
|---------------|-----------------|
|`RootFolder`|Opcjonalnie `string` parametr wejściowy.<br /><br /> Zawiera ścieżkę do folderu, który zawiera łącza miejsc docelowych.|
|`Files`|Opcjonalnie <xref:Microsoft.Build.Framework.ITaskItem> `[]` parametr wejściowy.<br /><br /> Zawiera przychodzącą listę plików.|
|`AssignedFiles`|Optional<br /><br /> <xref:Microsoft.Build.Framework.ITaskItem> `[]` Parametr wyjściowy.<br /><br /> Zawiera uzyskaną listę plików.|

## <a name="remarks"></a>Uwagi
Oprócz parametrów wymienionych powyżej, to zadanie dziedziczy parametry z <xref:Microsoft.Build.Tasks.TaskExtension> klasa, która sama dziedziczy <xref:Microsoft.Build.Utilities.Task> klasy. Aby uzyskać listę tych dodatkowych parametrów i ich opisów, zobacz [taskextension — klasa bazowa](../msbuild/taskextension-base-class.md).

## <a name="example"></a>Przykład
Poniższy przykład wykonuje `AssignTargetPath` zadanie, aby skonfigurować projekt.

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

## <a name="see-also"></a>Zobacz także
[Zadania](../msbuild/msbuild-tasks.md)  
[Odwołanie do zadania](../msbuild/msbuild-task-reference.md)
