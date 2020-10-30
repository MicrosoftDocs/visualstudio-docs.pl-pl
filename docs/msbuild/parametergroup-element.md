---
title: Element w parametrze | Microsoft Docs
description: Dowiedz się więcej o elemencie grupy parametrów programu MSBuild, który zawiera opcjonalną listę parametrów występujących w zadaniu wygenerowanym przez UsingTask TaskFactory.
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: 104a7313104e194a85d9eb4fee00e84a8facb5b5
ms.sourcegitcommit: 1a36533f385e50c05f661f440380fda6386ed3c1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2020
ms.locfileid: "93048869"
---
# <a name="parametergroup-element"></a>ParameterGroup, element

Zawiera opcjonalną listę parametrów, które będą obecne w zadaniu wygenerowanym przez `UsingTask` `TaskFactory` . Aby uzyskać więcej informacji, zobacz [UsingTask element (MSBuild)](../msbuild/usingtask-element-msbuild.md).

 \<Project> \<UsingTask>
 \<ParameterGroup>

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
|[Parametr](../msbuild/parameter-element.md)|Zawiera informacje dotyczące określonego parametru zadania, które jest generowane przez `UsingTask` `TaskFactory` . Nazwa elementu jest nazwą parametru.|

### <a name="parent-elements"></a>Elementy nadrzędne

| Element | Opis |
| - | - |
| [UsingTask](../msbuild/usingtask-element-msbuild.md) | Zapewnia sposób rejestrowania zadań w programie MSBuild. W projekcie może istnieć zero lub więcej `UsingTask` elementów. |

## <a name="example"></a>Przykład

 Poniższy przykład pokazuje, jak używać `ParameterGroup` elementu.

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
- [Dokumentacja zadań](../msbuild/msbuild-task-reference.md)
- [Odwołanie do schematu pliku projektu](../msbuild/msbuild-project-file-schema-reference.md)
