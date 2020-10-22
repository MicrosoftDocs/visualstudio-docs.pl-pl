---
title: CallTarget — — zadanie | Microsoft Docs
description: Dowiedz się, jak używać zadania MSBuild CallTarget — do wywoływania określonych elementów docelowych w pliku projektu.
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: efeca838050c9024ad3768b2ac7f73ce7dd06720
ms.sourcegitcommit: d3bca34f82de03fa34ecdd72233676c17fb3cb14
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/22/2020
ms.locfileid: "92353294"
---
# <a name="calltarget-task"></a>CallTarget — zadanie

Wywołuje określone elementy docelowe w pliku projektu.

## <a name="task-parameters"></a>Parametry zadania

 W poniższej tabeli opisano parametry `CallTarget` zadania.

| Parametr | Opis |
|---------------------------| - |
| `RunEachTargetSeparately` | Opcjonalny `Boolean` parametr wejściowy.<br /><br /> Jeśli `true` aparat MSBuild jest wywoływany raz na miejsce docelowe. Jeśli `false` aparat MSBuild jest wywoływany raz, aby skompilować wszystkie obiekty docelowe. Wartość domyślna to `false`. |
| `TargetOutputs` | Opcjonalny <xref:Microsoft.Build.Framework.ITaskItem> `[]` parametr wyjściowy.<br /><br /> Zawiera dane wyjściowe wszystkich skompilowanych elementów docelowych. |
| `Targets` | Opcjonalny `String[]` parametr.<br /><br /> Określa obiekt docelowy lub docelowy do skompilowania. |
| `UseResultsCache` | Opcjonalny `Boolean` parametr.<br /><br /> Jeśli `true` jest, zostanie zwrócony wynik z pamięci podręcznej, jeśli jest obecny.<br /><br /> **Uwaga** Po uruchomieniu zadania programu MSBuild jego dane wyjściowe są buforowane w zakresie (ProjectFileName, GlobalProperties) [TargetNames] jako listę elementów kompilacji. |

## <a name="remarks"></a>Uwagi

 Jeśli obiekt docelowy określony w polu `Targets` Niepowodzenie i `RunEachTargetSeparately` jest `true` , zadanie kontynuuje Kompilowanie pozostałych elementów docelowych.

 Jeśli chcesz skompilować domyślne elementy docelowe, użyj [zadania MSBuild](../msbuild/msbuild-task.md) i ustaw `Projects` parametr równy `$(MSBuildProjectFile)` .

W przypadku korzystania z programu `CallTarget` MSBuild ocenia wywołane miejsce docelowe w nowym zakresie, w przeciwieństwie do tego samego zakresu, z którego jest wywoływana. Oznacza to, że wszelkie zmiany elementów i właściwości w wywołanym miejscu docelowym nie są widoczne dla elementu docelowego wywołania.  Aby przekazać informacje do obiektu docelowego wywołującego, użyj `TargetOutputs` parametru Output.

 Oprócz parametrów wymienionych powyżej, to zadanie dziedziczy parametry z <xref:Microsoft.Build.Tasks.TaskExtension> klasy, która sama dziedziczy z <xref:Microsoft.Build.Utilities.Task> klasy. Aby zapoznać się z listą tych dodatkowych parametrów i ich opisów, zobacz [TaskExtension Base Class](../msbuild/taskextension-base-class.md).

## <a name="example"></a>Przykład

 Poniższy przykład wywołuje `TargetA` z wewnątrz `CallOtherTargets` .

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

- [Dokumentacja zadań](../msbuild/msbuild-task-reference.md)
- [Targets (Obiekty docelowe)](../msbuild/msbuild-targets.md)
