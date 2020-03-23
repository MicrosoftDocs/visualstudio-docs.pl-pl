---
title: Element grupy parametrów | Dokumenty firmy Microsoft
ms.date: 03/13/2017
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- <ParameterGroup> element [MSBuild]
- ParameterGroup element [MSBuild]
ms.assetid: c3275e69-a427-4889-bc1d-51bff2c285fa
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 8c06b9c530d3fff0fdfa429df633daaa4dde8c52
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "78263085"
---
# <a name="parametergroup-element"></a>Element Grupy parametrów

Zawiera opcjonalną listę parametrów, które będą obecne w `UsingTask` `TaskFactory`zadaniu generowanym przez program . Aby uzyskać więcej informacji, zobacz [UsingTask element (MSBuild)](../msbuild/usingtask-element-msbuild.md).

 \<> projektu \<UsingTask> \<ParameterGroup>

## <a name="syntax"></a>Składnia

```xml
<ParameterGroup />
```

## <a name="attributes-and-elements"></a>Atrybuty i elementy

 W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.

### <a name="attributes"></a>Atrybuty

 Brak.

### <a name="child-elements"></a>Elementy podrzędne

|Element|Opis|
|-------------|-----------------|
|[Parametr](../msbuild/parameter-element.md)|Zawiera informacje o określonym parametrze dla zadania `UsingTask` `TaskFactory`generowanego przez plik . Nazwa elementu jest nazwą parametru.|

### <a name="parent-elements"></a>Elementy nadrzędne

| Element | Opis |
| - | - |
| [Usingtask](../msbuild/usingtask-element-msbuild.md) | Umożliwia rejestrowanie zadań w msbuild. Może istnieć zero `UsingTask` lub więcej elementów w projekcie. |

## <a name="example"></a>Przykład

 W poniższym przykładzie `ParameterGroup` pokazano, jak używać elementu.

```xml
<UsingTask TaskName="MyTask" AssemblyName="My.Assembly" TaskFactory="MyTaskFactory">
       <ParameterGroup>
              <Parameter1 ParameterType="System.String" Required="False" Output="False"/>
              <Parameter2 ParameterType="System.Int" Required="True" Output="False"/>
             ...
</ParameterGroup>
       <Task Evaluate="true">
       ... Task factory-specific data ...
       </Task>
</UsingTask>
```

## <a name="see-also"></a>Zobacz też

- [Zadania](../msbuild/msbuild-tasks.md)
- [Odwołanie do zadania](../msbuild/msbuild-task-reference.md)
- [Odwołanie do schematu pliku projektu](../msbuild/msbuild-project-file-schema-reference.md)
