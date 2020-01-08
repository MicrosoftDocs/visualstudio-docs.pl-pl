---
title: Item, element (MSBuild) | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#ItemGroup
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- ItemGroup element [MSBuild]
- <ItemGroup> element [MSBuild]
ms.assetid: aac894e3-a9f1-4bbc-a796-6ef07001f35b
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 588118bf31c5d310e947b02fda476a63d0d9df7a
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/01/2020
ms.locfileid: "75573459"
---
# <a name="itemgroup-element-msbuild"></a>Item, element (MSBuild)
Zawiera zestaw [elementów zdefiniowanych przez](../msbuild/item-element-msbuild.md) użytkownika. Każdy element użyty w projekcie [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] musi być określony jako element podrzędny elementu `ItemGroup`.

\<Project > \<Items >

## <a name="syntax"></a>Składnia

```xml
<ItemGroup Condition="'String A' == 'String B'">
    <Item1>... </Item1>
    <Item2>... </Item2>
</ItemGroup>
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
|[Element](../msbuild/item-element-msbuild.md)|Definiuje dane wejściowe dla procesu kompilacji. W `ItemGroup`mogą znajdować się co najmniej zero elementów `Item`.|

### <a name="parent-elements"></a>Elementy nadrzędne

| Element | Opis |
| - | - |
| [Project](../msbuild/project-element-msbuild.md) | Wymagany element główny pliku projektu [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)]. |
| [Cel](../msbuild/target-element-msbuild.md) | Począwszy od .NET Framework 3,5, element `ItemGroup` może znajdować się wewnątrz elementu `Target`. Aby uzyskać więcej informacji, zobacz [targets](../msbuild/msbuild-targets.md). |

## <a name="example"></a>Przykład
Poniższy przykład kodu przedstawia zdefiniowane przez użytkownika kolekcje elementów `Res` i `CodeFiles` zadeklarowane wewnątrz elementu `ItemGroup`. Każdy element w kolekcji `Res` elementów zawiera zdefiniowany przez użytkownika element podrzędny [ItemMetadata —](../msbuild/itemmetadata-element-msbuild.md) .

```xml
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
    <ItemGroup>
        <Res Include = "Strings.fr.resources" >
            <Culture>fr</Culture>
        </Res>
        <Res Include = "Dialogs.fr.resources" >
            <Culture>fr</Culture>
        </Res>

        <CodeFiles Include="**\*.cs" Exclude="**\generated\*.cs" />
        <CodeFiles Include="..\..\Resources\Constants.cs" />
    </ItemGroup>
...
</Project>
```

## <a name="see-also"></a>Zobacz także
- [Odwołanie do schematu pliku projektu](../msbuild/msbuild-project-file-schema-reference.md)
- [Elementy](../msbuild/msbuild-items.md)
- [Wspólne elementy projektu MSBuild](../msbuild/common-msbuild-project-items.md)
