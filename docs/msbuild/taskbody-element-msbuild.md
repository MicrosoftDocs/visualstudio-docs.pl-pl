---
title: TaskBody — — element (MSBuild) | Microsoft Docs
ms.date: 03/13/2017
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- TaskBody element [MSBuild]
- <TaskBody> element [MSBuild]
ms.assetid: 49d8741b-f1ea-4470-94fd-a1ac27341a6a
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 45b255f782390cfc478ac2f7bce58170e4e2b268
ms.sourcegitcommit: 96737c54162f5fd5c97adef9b2d86ccc660b2135
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/26/2020
ms.locfileid: "77631851"
---
# <a name="taskbody-element-msbuild"></a>TaskBody —, element (MSBuild)

Zawiera dane, które są przesyłane do `TaskFactory``UsingTask`. Aby uzyskać więcej informacji, zobacz [UsingTask element (MSBuild)](../msbuild/usingtask-element-msbuild.md).

 \<Project > \<UsingTask > \<TaskBody — >

## <a name="syntax"></a>Składnia

```xml
<TaskBody Evaluate="true/false" />
```

## <a name="attributes-and-elements"></a>Atrybuty i elementy

 W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.

### <a name="attributes"></a>Atrybuty

|Atrybut|Opis|
|---------------|-----------------|
|`Evaluate`|Opcjonalny logiczny atrybut.<br /><br /> Jeśli `true`, MSBuild oblicza wszystkie elementy wewnętrzne i rozszerza elementy i właściwości przed przekazaniem informacji do `TaskFactory` podczas tworzenia wystąpienia zadania.|

### <a name="child-elements"></a>Elementy podrzędne

|Element|Opis|
|-------------|-----------------|
|Dane|Tekst między tagami `TaskBody` jest wysyłany Verbatim do `TaskFactory`.|

### <a name="parent-elements"></a>Elementy nadrzędne

| Element | Opis |
| - | - |
| [UsingTask](../msbuild/usingtask-element-msbuild.md) | Zapewnia sposób rejestrowania zadań w programie MSBuild. W projekcie może istnieć co najmniej zero elementów `UsingTask`. |

## <a name="example"></a>Przykład

 Poniższy przykład pokazuje, jak używać elementu `TaskBody` z atrybutem `Evaluate`.

```xml
<UsingTask TaskName="MyTask" AssemblyName="My.Assembly" TaskFactory="MyTaskFactory">
       <ParameterGroup>
              <Parameter1 ParameterType="System.String" Required="False" Output="False"/>
              <Parameter2 ParameterType="System.Int" Required="True" Output="False"/>
              ...
</ParameterGroup>
       <TaskBody Evaluate="true">
      ... Task factory-specific data ...
       </TaskBody>
</UsingTask>
```

## <a name="see-also"></a>Zobacz też

- [Zadania](../msbuild/msbuild-tasks.md)
- [Odwołanie do zadania](../msbuild/msbuild-task-reference.md)
- [Odwołanie do schematu pliku projektu](../msbuild/msbuild-project-file-schema-reference.md)
