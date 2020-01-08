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
ms.openlocfilehash: 8d7e77e56196d23a5563c60d5b8251c8f26a00ff
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/01/2020
ms.locfileid: "75596739"
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

### <a name="attributes"></a>{1&gt;{2&gt;Atrybuty&lt;2}&lt;1}
 Brak.

### <a name="child-elements"></a>Elementy podrzędne

|Element|Opis|
|-------------|-----------------|
|[Parametr](../msbuild/parameter-element.md)|Zawiera informacje dotyczące konkretnego parametru zadania generowanego przez `TaskFactory``UsingTask`. Nazwa elementu jest nazwą parametru.|

### <a name="parent-elements"></a>Elementy nadrzędne

| Element | Opis |
| - | - |
| [UsingTask](../msbuild/usingtask-element-msbuild.md) | Zapewnia sposób rejestrowania zadań w [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)]. W projekcie może istnieć co najmniej zero elementów `UsingTask`. |

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

## <a name="see-also"></a>Zobacz także
- [Zadania](../msbuild/msbuild-tasks.md)
- [Odwołanie do zadania](../msbuild/msbuild-task-reference.md)
- [Odwołanie do schematu pliku projektu](../msbuild/msbuild-project-file-schema-reference.md)
