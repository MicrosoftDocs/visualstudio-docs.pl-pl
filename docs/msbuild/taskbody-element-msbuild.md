---
title: Element zadania usingTask (MSBuild) | Dokumenty firmy Microsoft
ms.date: 03/13/2017
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- Task element [MSBuild]
- <Task> element [MSBuild]
ms.assetid: 49d8741b-f1ea-4470-94fd-a1ac27341a6a
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 36644a6b21092361d92dba5f0886eb4198884995
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "78263191"
---
# <a name="task-element-of-usingtask-msbuild"></a>Element zadania UsingTask (MSBuild)

Zawiera dane przekazywane do `UsingTask` `TaskFactory`pliku . Aby uzyskać więcej informacji, zobacz [UsingTask element (MSBuild)](../msbuild/usingtask-element-msbuild.md).

 \<>> \<projektu usingTask> \<task>

## <a name="syntax"></a>Składnia

```xml
<Task Evaluate="true/false" />
```

## <a name="attributes-and-elements"></a>Atrybuty i elementy

 W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.

### <a name="attributes"></a>Atrybuty

|Atrybut|Opis|
|---------------|-----------------|
|`Evaluate`|Opcjonalny atrybut logiczny.<br /><br /> Jeśli `true`, MSBuild ocenia wszystkie elementy wewnętrzne i rozwija elementy i właściwości, zanim przekazuje informacje `TaskFactory` do, gdy zadanie jest tworzone.|

### <a name="child-elements"></a>Elementy podrzędne

|Element|Opis|
|-------------|-----------------|
|Dane|Tekst między `Task` znacznikami jest wysyłany dosłownie `TaskFactory`do pliku .|

### <a name="parent-elements"></a>Elementy nadrzędne

| Element | Opis |
| - | - |
| [Usingtask](../msbuild/usingtask-element-msbuild.md) | Umożliwia rejestrowanie zadań w msbuild. Może istnieć zero `UsingTask` lub więcej elementów w projekcie. |

## <a name="example"></a>Przykład

 W poniższym przykładzie `Task` pokazano, `Evaluate` jak używać elementu z atrybutem.

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
