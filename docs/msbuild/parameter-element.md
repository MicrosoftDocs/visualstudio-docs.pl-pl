---
title: Element parametru | Microsoft Docs
description: Dowiedz się więcej na temat elementu parametru MSBuild, który zawiera informacje o określonym parametrze dla zadania wygenerowanego przez UsingTask TaskFactory.
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 728618a6d9ff174d4d4bf7cdc20516433d06036b
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99918867"
---
# <a name="parameter-element"></a>Parameter, element

Zawiera informacje dotyczące określonego parametru zadania, które jest generowane przez `UsingTask` `TaskFactory` .  Nazwa elementu jest nazwą parametru.  Aby uzyskać więcej informacji, zobacz [UsingTask element (MSBuild)](../msbuild/usingtask-element-msbuild.md).

 \<Project> \<UsingTask>
 \<ParameterGroup>
 \<Parameter>

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
|`ParameterType`|Atrybut opcjonalny.<br /><br /> Typ .NET parametru, na przykład `System.String` .|
|`Output`|Opcjonalny atrybut Boolean.<br /><br /> Jeśli `true` , ten parametr jest parametrem wyjściowym zadania. Domyślna wartość to `false`.|
|`Required`|Opcjonalny atrybut Boolean.<br /><br /> Jeśli `true` , ten parametr jest wymaganym parametrem zadania. Domyślna wartość to `false`.|

### <a name="child-elements"></a>Elementy podrzędne

 Brak.

### <a name="parent-elements"></a>Elementy nadrzędne

|Element|Opis|
|-------------|-----------------|
|[ParameterGroup —](../msbuild/parametergroup-element.md)|Zawiera opcjonalną listę parametrów, które będą obecne w zadaniu wygenerowanym przez `UsingTask` `TaskFactory` .|

## <a name="example"></a>Przykład

 Poniższy przykład pokazuje, jak używać `Parameter` elementu.

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
