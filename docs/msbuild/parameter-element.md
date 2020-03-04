---
title: Element parametru | Microsoft Docs
ms.date: 03/13/2017
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
- xml
helpviewer_keywords:
- Parameter element [MSBuild]
- <Parameter> element [MSBuild]
ms.assetid: b273afff-b500-4e97-8cfd-31f39fa64a51
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: dbf0c25967d84e930ee97a84709c808d3541e733
ms.sourcegitcommit: 3ed59ce39692124fe61c484df4348c0b9abee9b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/04/2020
ms.locfileid: "78263111"
---
# <a name="parameter-element"></a>Parameter, element

Zawiera informacje dotyczące konkretnego parametru zadania generowanego przez `TaskFactory``UsingTask`.  Nazwa elementu jest nazwą parametru.  Aby uzyskać więcej informacji, zobacz [UsingTask element (MSBuild)](../msbuild/usingtask-element-msbuild.md).

 \<Project > \<UsingTask > \<, > \<parametr >

## <a name="syntax"></a>Składnia

```xml
<ParameterGroup ParameterType="SystemType"
    Output="true/false"
    Required="true/false" />
```

## <a name="attributes-and-elements"></a>Atrybuty i elementy

 W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.

### <a name="attributes"></a>Atrybuty

|Atrybut|Opis|
|---------------|-----------------|
|`ParameterType`|Atrybut opcjonalny.<br /><br /> Typ .NET parametru, na przykład `System.String`.|
|`Output`|Opcjonalny logiczny atrybut.<br /><br /> Jeśli `true`, ten parametr jest parametrem wyjściowym zadania. Domyślna wartość to `false`.|
|`Required`|Opcjonalny logiczny atrybut.<br /><br /> Jeśli `true`, ten parametr jest wymaganym parametrem zadania. Domyślna wartość to `false`.|

### <a name="child-elements"></a>Elementy podrzędne

 Brak.

### <a name="parent-elements"></a>Elementy nadrzędne

|Element|Opis|
|-------------|-----------------|
|[ParameterGroup —](../msbuild/parametergroup-element.md)|Zawiera opcjonalną listę parametrów, które będą obecne w zadaniu generowanym przez `UsingTask` `TaskFactory`.|

## <a name="example"></a>Przykład

 Poniższy przykład pokazuje, jak używać elementu `Parameter`.

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
