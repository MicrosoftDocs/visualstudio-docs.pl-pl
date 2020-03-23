---
title: Element ItemGroup (MSBuild) | Dokumenty firmy Microsoft
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
ms.openlocfilehash: 8064ce4c13419238ca5877893a731d2ac53afb25
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "77633645"
---
# <a name="itemgroup-element-msbuild"></a>Element ItemGroup (MSBuild)

Zawiera zestaw elementów [elementu](../msbuild/item-element-msbuild.md) zdefiniowanego przez użytkownika. Każdy element używany w projekcie MSBuild musi być `ItemGroup` określony jako element podrzędny elementu.

\<> \<> itemgroup projektu

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
|`Condition`|Atrybut opcjonalny. Warunek do oceny. Aby uzyskać więcej informacji, zobacz [Warunki](../msbuild/msbuild-conditions.md).|
|`Label`|Atrybut opcjonalny. Identyfikuje plik `ItemGroup`.|

### <a name="child-elements"></a>Elementy podrzędne

|Element|Opis|
|-------------|-----------------|
|[Element](../msbuild/item-element-msbuild.md)|Definiuje dane wejściowe dla procesu kompilacji. W pliku `Item` `ItemGroup`.|

### <a name="parent-elements"></a>Elementy nadrzędne

| Element | Opis |
| - | - |
| [Project](../msbuild/project-element-msbuild.md) | Wymagany element główny pliku projektu MSBuild. |
| [Obiekt docelowy](../msbuild/target-element-msbuild.md) | Począwszy od .NET Framework 3.5, `ItemGroup` `Target` element może pojawić się wewnątrz elementu. Aby uzyskać więcej informacji, zobacz [Cele](../msbuild/msbuild-targets.md). |

## <a name="example"></a>Przykład

Poniższy przykład kodu pokazuje kolekcje `Res` elementów zdefiniowanych przez użytkownika i `CodeFiles` zadeklarowane wewnątrz `ItemGroup` elementu. Każdy z elementów `Res` w kolekcji elementów zawiera element podrzędny zdefiniowany przez użytkownika [element podrzędny ItemMetadata.](../msbuild/itemmetadata-element-msbuild.md)

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
- [Items](../msbuild/msbuild-items.md)
- [Typowe elementy projektu MSBuild](../msbuild/common-msbuild-project-items.md)
