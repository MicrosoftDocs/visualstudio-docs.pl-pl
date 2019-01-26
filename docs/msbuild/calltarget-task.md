---
title: Calltarget — zadanie | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- CallTarget task [MSBuild]
- MSBuild, CallTarget task
ms.assetid: bb1fe2c4-4383-436f-8326-c24cc4a46150
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 85ad6261dba80e56ab44f43b4c70df79d63bb509
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/25/2019
ms.locfileid: "55001634"
---
# <a name="calltarget-task"></a>CallTarget — zadanie
Wywołuje określonych celów w pliku projektu.  

## <a name="task-parameters"></a>Parametry zadania  
 W poniższej tabeli opisano parametry `CallTarget` zadania.  


| Parametr | Opis |
|---------------------------| - |
| `RunEachTargetSeparately` | Opcjonalnie `Boolean` parametr wejściowy.<br /><br /> Jeśli `true`, [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] aparat jest wywoływana jeden raz na docelowym. Jeśli `false`, [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] aparat jest wywoływana jeden raz do tworzenia wszystkich obiektów docelowych. Wartość domyślna to `false`. |
| `TargetOutputs` | Opcjonalnie <xref:Microsoft.Build.Framework.ITaskItem> `[]` parametr wyjściowy.<br /><br /> Zawiera dane wyjściowe wszystkich skompilowanych elementów docelowych. |
| `Targets` | Opcjonalnie `String[]` parametru.<br /><br /> Określa cel lub cele do kompilacji. |
| `UseResultsCache` | Opcjonalnie `Boolean` parametru.<br /><br /> Jeśli `true`, buforowane wynik jest zwracany, jeśli jest obecny.<br /><br /> **Uwaga** podczas MSBuild, zadanie zostanie uruchomione, dane wyjściowe są buforowane w zakresie (ProjectFileName, GlobalProperties) [TargetNames] jako listę elementów kompilacji. |

## <a name="remarks"></a>Uwagi  
 Jeśli obiekt docelowy określony w `Targets` kończy się niepowodzeniem i `RunEachTargetSeparately` jest `true`, zadania w dalszym ciągu kompilacji pozostałe elementy docelowe.  

 Do kompilacji domyślnych elementów docelowych, należy użyć [zadanie MSBuild](../msbuild/msbuild-task.md) i ustaw `Projects` równa parametr `$(MSBuildProjectFile)`.  

 Oprócz parametrów wymienionych powyżej, to zadanie dziedziczy parametry z <xref:Microsoft.Build.Tasks.TaskExtension> klasa, która sama dziedziczy <xref:Microsoft.Build.Utilities.Task> klasy. Aby uzyskać listę tych dodatkowych parametrów i ich opisów, zobacz [taskextension — klasa bazowa](../msbuild/taskextension-base-class.md).  

## <a name="example"></a>Przykład  
 Poniższy przykład wywołuje `TargetA` z wewnątrz `CallOtherTargets`.  

```xml  
<Project DefaultTargets="CallOtherTargets"  
    xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  

    <Target Name="CallOtherTargets">  
        <CallTarget Targets="TargetA"/>  
    </Target>  

    <Target Name="TargetA">  
        <Message Text="Building TargetA..." />  
    </Target>  

</Project>  
```  

## <a name="see-also"></a>Zobacz także  
 [Odwołanie do zadania](../msbuild/msbuild-task-reference.md)   
 [Docelowe elementy](../msbuild/msbuild-targets.md)