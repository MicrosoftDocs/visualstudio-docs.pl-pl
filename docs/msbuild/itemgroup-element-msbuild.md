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
ms.openlocfilehash: cd21d7da710a82d9396766971244aa5f7f9bbd4d
ms.sourcegitcommit: 68f893f6e472df46f323db34a13a7034dccad25a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/15/2020
ms.locfileid: "77278794"
---
# <a name="itemgroup-element-msbuild"></a>Item, element (MSBuild)
Zawiera zestaw [elementów zdefiniowanych przez](../msbuild/item-element-msbuild.md) użytkownika. Każdy element użyty w projekcie [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] musi być określony jako element podrzędny elementu `ItemGroup`.

\<Project > \<Items >

## <a name="syntax"></a>Składnia

```xml
<ItemGroup Condition="'String A' == 'String B'"
           Label="Label">
    <Item1>... </Item1>
    <Item2>... </Item2>
</ItemGroup>
```

## <a name="attributes-and-elements"></a>Atrybuty i elementy
W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.

### <a name="attributes"></a>Atrybuty

|Atrybut|Opis|
|---------------|-----------------|
|`Condition`|Atrybut opcjonalny. Warunek do obliczenia. Aby uzyskać więcej informacji, zobacz [warunki](../msbuild/msbuild-conditions.md).|
|`Label`|Atrybut opcjonalny. Identyfikuje `ItemGroup`.|

### <a name="child-elements"></a>Elementy podrzędne

|Element|Opis|
|-------------|-----------------|
|[Element](../msbuild/item-element-msbuild.md)|Definiuje dane wejściowe dla procesu kompilacji. W `ItemGroup`mogą znajdować się co najmniej zero elementów `Item`.|

### <a name="parent-elements"></a>Elementy nadrzędne

| Element | Opis |
| - | - |
| [Projektu](../msbuild/project-element-msbuild.md) | Wymagany element główny pliku projektu [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)]. |
| [Obiekt docelowy](../msbuild/target-element-msbuild.md) | Począwszy od .NET Framework 3,5, element `ItemGroup` może znajdować się wewnątrz elementu `Target`. Aby uzyskać więcej informacji, zobacz [targets](../msbuild/msbuild-targets.md). |

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

## <a name="see-also"></a>Zobacz też
- [Odwołanie do schematu pliku projektu](../msbuild/msbuild-project-file-schema-reference.md)
- [Elementy](../msbuild/msbuild-items.md)
- [Wspólne elementy projektu MSBuild](../msbuild/common-msbuild-project-items.md)
