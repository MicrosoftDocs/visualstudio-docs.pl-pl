---
title: CallTarget — — zadanie | Microsoft Docs
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
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 831153a734fa88c045f7b8397db0a033e53862c7
ms.sourcegitcommit: 96737c54162f5fd5c97adef9b2d86ccc660b2135
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/26/2020
ms.locfileid: "77634490"
---
# <a name="calltarget-task"></a>CallTarget — zadanie

Wywołuje określone elementy docelowe w pliku projektu.

## <a name="task-parameters"></a>Parametry zadania

 W poniższej tabeli opisano parametry zadania `CallTarget`.

| Parametr | Opis |
|---------------------------| - |
| `RunEachTargetSeparately` | Opcjonalny `Boolean` parametr wejściowy.<br /><br /> Jeśli `true`, aparat MSBuild jest wywoływany raz na miejsce docelowe. Jeśli `false`, aparat MSBuild jest wywoływana raz, aby skompilować wszystkie obiekty docelowe. Wartością domyślną jest `false`. |
| `TargetOutputs` | Opcjonalny <xref:Microsoft.Build.Framework.ITaskItem>`[]` parametr wyjściowy.<br /><br /> Zawiera dane wyjściowe wszystkich skompilowanych elementów docelowych. |
| `Targets` | Opcjonalny parametr `String[]`.<br /><br /> Określa obiekt docelowy lub docelowy do skompilowania. |
| `UseResultsCache` | Opcjonalny parametr `Boolean`.<br /><br /> Jeśli `true`, buforowany wynik jest zwracany, jeśli jest obecny.<br /><br /> **Uwaga** Po uruchomieniu zadania programu MSBuild jego dane wyjściowe są buforowane w zakresie (ProjectFileName, GlobalProperties) [TargetNames] jako listę elementów kompilacji. |

## <a name="remarks"></a>Uwagi

 Jeśli obiekt docelowy określony w `Targets` kończy się niepowodzeniem i `RunEachTargetSeparately` jest `true`, zadanie kontynuuje Kompilowanie pozostałych elementów docelowych.

 Jeśli chcesz skompilować domyślne elementy docelowe, użyj [zadania MSBuild](../msbuild/msbuild-task.md) i ustaw parametr `Projects` równe `$(MSBuildProjectFile)`.

 Oprócz parametrów wymienionych powyżej, to zadanie dziedziczy parametry z klasy <xref:Microsoft.Build.Tasks.TaskExtension>, która sama dziedziczy z klasy <xref:Microsoft.Build.Utilities.Task>. Aby zapoznać się z listą tych dodatkowych parametrów i ich opisów, zobacz [TaskExtension Base Class](../msbuild/taskextension-base-class.md).

## <a name="example"></a>Przykład

 Poniższy przykład wywołuje `TargetA` od wewnątrz `CallOtherTargets`.

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

## <a name="see-also"></a>Zobacz też

- [Odwołanie do zadania](../msbuild/msbuild-task-reference.md)
- [Docelowe elementy](../msbuild/msbuild-targets.md)
