---
title: CallTarget — — zadanie | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
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
caps.latest.revision: 9
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 9093b35cc444fc0b346f81a91d20afe73bd476cd
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "68160426"
---
# <a name="calltarget-task"></a>CallTarget — Zadanie
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Wywołuje określone elementy docelowe w pliku projektu.  
  
## <a name="task-parameters"></a>Parametry zadania  
 W poniższej tabeli opisano parametry `CallTarget` zadania.  
  
|Parametr|Opis|  
|---------------|-----------------|  
|`RunEachTargetSeparately`|Opcjonalny `Boolean` parametr wyjściowy.<br /><br /> Jeśli `true` [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] aparat jest wywoływany raz na miejsce docelowe. Jeśli `false` [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] aparat jest wywoływana raz, aby skompilować wszystkie obiekty docelowe. Wartość domyślna to `false`.|  
|`TargetOutputs`|Opcjonalny <xref:Microsoft.Build.Framework.ITaskItem> `[]` parametr wyjściowy.<br /><br /> Zawiera dane wyjściowe wszystkich skompilowanych elementów docelowych.|  
|`Targets`|Opcjonalny `String[]` parametr.<br /><br /> Określa obiekt docelowy lub docelowy do skompilowania.|  
|`UseResultsCache`|Opcjonalny `Boolean` parametr.<br /><br /> Jeśli `true` jest, zostanie zwrócony wynik z pamięci podręcznej, jeśli jest obecny.<br /><br /> **Uwaga** Po uruchomieniu zadania programu MSBuild jego dane wyjściowe są buforowane w zakresie (ProjectFileName, GlobalProperties) [TargetNames] jako listę elementów kompilacji.|  
  
## <a name="remarks"></a>Uwagi  
 Jeśli obiekt docelowy określony w polu `Targets` Niepowodzenie i `RunEachTargetSeparately` jest `true` , zadanie kontynuuje Kompilowanie pozostałych elementów docelowych.  
  
 Jeśli chcesz skompilować domyślne elementy docelowe, użyj [zadania MSBuild](../msbuild/msbuild-task.md) i ustaw `Projects` parametr równy `$(MSBuildProjectFile)` .  
  
 Oprócz parametrów wymienionych powyżej, to zadanie dziedziczy parametry z <xref:Microsoft.Build.Tasks.TaskExtension> klasy, która sama dziedziczy z <xref:Microsoft.Build.Utilities.Task> klasy. Aby zapoznać się z listą tych dodatkowych parametrów i ich opisów, zobacz [TaskExtension Base Class](../msbuild/taskextension-base-class.md).  
  
## <a name="example"></a>Przykład  
 Poniższy przykład wywołuje `TargetA` z wewnątrz `CallOtherTargets` .  
  
```  
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
  
## <a name="see-also"></a>Zobacz też  
 [Odwołanie do zadania](../msbuild/msbuild-task-reference.md)   
 [Targets (Obiekty docelowe)](../msbuild/msbuild-targets.md)
