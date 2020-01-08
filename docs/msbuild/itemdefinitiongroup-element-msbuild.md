---
title: ItemDefinitionGroup — element (MSBuild) | Microsoft Docs
ms.date: 03/13/2017
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#ItemDefinitionGroup
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- ItemDefinitionGroup Element [MSBuild]
- <ItemDefinitionGroup> Element [MSBuild]
ms.assetid: 4e9fb04b-5148-4ae5-a394-42861dd62371
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: c5bfe09fec169495afa5b58a41f7c9f1b9bacfad
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/01/2020
ms.locfileid: "75573472"
---
# <a name="itemdefinitiongroup-element-msbuild"></a>ItemDefinitionGroup, element (MSBuild)
Element `ItemDefinitionGroup` umożliwia zdefiniowanie zestawu definicji elementów, które są wartościami metadanych, które są stosowane do wszystkich elementów w projekcie, domyślnie. ItemDefinitionGroup zastępuje potrzebę korzystania z [zadania elementu](../msbuild/createitem-task.md) a i [zadania właściwości](../msbuild/createproperty-task.md). Aby uzyskać więcej informacji, zobacz [definicje elementu](../msbuild/item-definitions.md).

\<Project> \<ItemDefinitionGroup>

## <a name="syntax"></a>Składnia

```xml
<ItemDefinitionGroup Condition="'String A' == 'String B'">
    <Item1>... </Item1>
    <Item2>... </Item2>
</ItemDefinitionGroup>
```

## <a name="attributes-and-elements"></a>Atrybuty i elementy
W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.

### <a name="attributes"></a>{1&gt;{2&gt;Atrybuty&lt;2}&lt;1}

|Atrybut|Opis|
|---------------|-----------------|
|`Condition`|Atrybut opcjonalny. Warunek do obliczenia. Aby uzyskać więcej informacji, zobacz [warunki](../msbuild/msbuild-conditions.md).|

### <a name="child-elements"></a>Elementy podrzędne

|Element|Opis|
|-------------|-----------------|
|[Element](../msbuild/item-element-msbuild.md)|Definiuje dane wejściowe dla procesu kompilacji. W `ItemDefinitionGroup`mogą znajdować się co najmniej zero elementów `Item`.|

### <a name="parent-elements"></a>Elementy nadrzędne

| Element | Opis |
| - | - |
| [Project](../msbuild/project-element-msbuild.md) | Wymagany element główny pliku projektu [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)]. |

## <a name="example"></a>Przykład
Poniższy przykład kodu definiuje dwa elementy metadanych, m i n, w ItemDefinitionGroup. W tym przykładzie domyślne metadane "m" są stosowane do elementu "i", ponieważ metadane "m" nie są jawnie zdefiniowane przez element "i". Jednak domyślne metadane "n" nie są stosowane do elementu "i", ponieważ metadane "n" są już zdefiniowane przez element "i".

```xml
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
    <ItemDefinitionGroup>
        <i>
            <m>m1</m>
            <n>n1</n>
        </i>
    </ItemDefinitionGroup>
    <ItemGroup>
        <i Include="a">
            <o>o1</o>
            <n>n2</n>
        </i>
    </ItemGroup>
    ...
</Project>
```

## <a name="see-also"></a>Zobacz także
- [Odwołanie do schematu pliku projektu](../msbuild/msbuild-project-file-schema-reference.md)
- [Elementy](../msbuild/msbuild-items.md)
