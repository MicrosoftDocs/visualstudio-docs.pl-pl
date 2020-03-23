---
title: Zadanie Przypisz docelową ścieżkę | Dokumenty firmy Microsoft
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
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "77634542"
---
# <a name="assigntargetpath-task"></a>Zadanie Przypisz ścieżkę docelową

To zadanie akceptuje listę plików `<TargetPath>` i dodaje atrybuty, jeśli nie zostały jeszcze określone.

## <a name="task-parameters"></a>Parametry zadania

W poniższej tabeli `AssignTargetPath` opisano parametry zadania.

|Parametr|Opis|
|---------------|-----------------|
|`RootFolder`|Opcjonalny `string` parametr wejściowy.<br /><br /> Zawiera ścieżkę do folderu zawierającego łącza docelowe.|
|`Files`|Opcjonalny <xref:Microsoft.Build.Framework.ITaskItem> `[]` parametr wejściowy.<br /><br /> Zawiera przychodzącą listę plików.|
|`AssignedFiles`|Optional (Opcjonalność)<br /><br /> <xref:Microsoft.Build.Framework.ITaskItem>`[]` parametru wyjściowego.<br /><br /> Zawiera wynikową listę plików.|

## <a name="remarks"></a>Uwagi

Oprócz parametrów wymienionych powyżej, to zadanie dziedziczy parametry z <xref:Microsoft.Build.Tasks.TaskExtension> klasy, <xref:Microsoft.Build.Utilities.Task> która sama dziedziczy z klasy. Aby uzyskać listę tych dodatkowych parametrów i ich opisy, zobacz [TaskExtension klasy podstawowej](../msbuild/taskextension-base-class.md).

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

## <a name="see-also"></a>Zobacz też

- [Zadania](../msbuild/msbuild-tasks.md)
- [Odwołanie do zadania](../msbuild/msbuild-task-reference.md)
