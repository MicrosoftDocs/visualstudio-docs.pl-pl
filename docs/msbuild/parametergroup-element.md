---
title: Element w parametrze | Microsoft Docs
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
ms.openlocfilehash: 28d6def203a819d41a420899663d1a974612c631
ms.sourcegitcommit: 96737c54162f5fd5c97adef9b2d86ccc660b2135
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/26/2020
ms.locfileid: "77632995"
---
# <a name="parametergroup-element"></a>Element DataParameter

Zawiera opcjonalną listę parametrów, które będą obecne w zadaniu generowanym przez `UsingTask` `TaskFactory`. Aby uzyskać więcej informacji, zobacz [UsingTask element (MSBuild)](../msbuild/usingtask-element-msbuild.md).

 \<Project > \<UsingTask > \<parametr >

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
|[Konstruktora](../msbuild/parameter-element.md)|Zawiera informacje dotyczące konkretnego parametru zadania generowanego przez `TaskFactory``UsingTask`. Nazwa elementu jest nazwą parametru.|

### <a name="parent-elements"></a>Elementy nadrzędne

| Element | Opis |
| - | - |
| [UsingTask](../msbuild/usingtask-element-msbuild.md) | Zapewnia sposób rejestrowania zadań w programie MSBuild. W projekcie może istnieć co najmniej zero elementów `UsingTask`. |

## <a name="example"></a>Przykład

 Poniższy przykład pokazuje, jak używać elementu `ParameterGroup`.

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
