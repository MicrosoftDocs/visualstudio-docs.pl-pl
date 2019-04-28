---
title: ItemDefinitionGroup — Element (MSBuild) | Dokumentacja firmy Microsoft
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
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 130683b114c4601de209ec5f86b7b6f3e8bed027
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "63001192"
---
# <a name="itemdefinitiongroup-element-msbuild"></a>ItemDefinitionGroup — element (MSBuild)
`ItemDefinitionGroup` Element umożliwia zdefiniowanie zestawu definicji elementów, które są wartości metadanych, które są stosowane do wszystkich elementów w projekcie, domyślnie. ItemDefinitionGroup — zastępuje konieczność stosowania [createitem — zadanie](../msbuild/createitem-task.md) i [CreateProperty — zadanie](../msbuild/createproperty-task.md). Aby uzyskać więcej informacji, zobacz [definicje elementów](../msbuild/item-definitions.md).

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

### <a name="attributes"></a>Atrybuty

|Atrybut|Opis|
|---------------|-----------------|
|`Condition`|Atrybut opcjonalny. Warunek, który ma zostać obliczone. Aby uzyskać więcej informacji, zobacz [warunki](../msbuild/msbuild-conditions.md).|

### <a name="child-elements"></a>Elementy podrzędne

|Element|Opis|
|-------------|-----------------|
|[Element](../msbuild/item-element-msbuild.md)|Definiuje dane wejściowe dla procesu kompilacji. Może wynosić zero lub więcej `Item` elementów w `ItemDefinitionGroup`.|

### <a name="parent-elements"></a>Elementy nadrzędne

| Element | Opis |
| - | - |
| [Project](../msbuild/project-element-msbuild.md) | Element główny wymagany [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] pliku projektu. |

## <a name="example"></a>Przykład
Poniższy kod definiuje dwa elementy metadanych, m, n, a w ItemDefinitionGroup —. W tym przykładzie domyślne metadanych "m" jest stosowany do elementu "i", ponieważ metadane "m" nie jest jawnie zdefiniowany przez element "i". Jednak domyślne metadanych "n" nie ma zastosowania do elementu "i", ponieważ metadane "n" jest już zdefiniowany przez element "i".

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
