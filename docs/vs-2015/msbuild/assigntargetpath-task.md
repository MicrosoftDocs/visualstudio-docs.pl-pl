---
title: AssignTargetPath — Zadanie | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
ms.assetid: 0e830e31-3bcf-4259-b2a8-a5df49b92d51
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: f7bf12e9f6c90ce544205370a8ed26440388b0a6
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "68187015"
---
# <a name="assigntargetpath-task"></a>AssignTargetPath — Zadanie
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

To zadanie akceptuje pliki list i dodaje `<TargetPath>` atrybuty, jeśli nie zostały one jeszcze określone.  
  
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
  
```  
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
 [Widoku](../msbuild/msbuild-tasks.md)   
 [Odwołanie do zadania](../msbuild/msbuild-task-reference.md)
