---
title: ItemMetadata — — element (MSBuild) | Microsoft Docs
ms.date: 03/13/2017
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- ItemMetadata Element [MSBuild]
- <ItemMetadata> Element [MSBuild]
ms.assetid: e3db5122-202d-43a9-b2f4-3e0ec4ed3d08
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 66c19dbd74176babbf9e26030a68a6095992b660
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/01/2020
ms.locfileid: "75589373"
---
# <a name="itemmetadata-element-msbuild"></a>ItemMetadata —, element (MSBuild)
Zawiera klucz metadanych elementu zdefiniowanego przez użytkownika, który zawiera wartość metadanych elementu. Element może mieć dowolną liczbę par klucz-wartość metadanych.

 \<Project > \<Itemmanager > \<

## <a name="syntax"></a>Składnia

```xml
<ItemMetadataName> Item Metadata value</ItemMetadataName>
```

## <a name="attributes-and-elements"></a>Atrybuty i elementy
 W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.

### <a name="attributes"></a>{1&gt;{2&gt;Atrybuty&lt;2}&lt;1}

|Atrybut|Opis|
|---------------|-----------------|
|`Condition`|Atrybut opcjonalny.<br /><br /> Warunek do obliczenia. Aby uzyskać więcej informacji, zobacz [warunki](../msbuild/msbuild-conditions.md).|

### <a name="child-elements"></a>Elementy podrzędne
 Brak.

### <a name="parent-elements"></a>Elementy nadrzędne

|Element|Opis|
|-------------|-----------------|
|[Element](../msbuild/item-element-msbuild.md)|Element zdefiniowany przez użytkownika, który definiuje dane wejściowe dla procesu kompilacji.|

## <a name="text-value"></a>Wartość tekstowa
 Wartość tekstowa jest opcjonalna.

 Ten tekst Określa wartość metadanych elementu, która może być tekstem lub XML.

## <a name="example"></a>Przykład
 Poniższy przykład kodu pokazuje, jak dodać `Culture` metadanych z wartością `fr` do `CSFile`elementu.

```xml
<ItemGroup>
    <CSFile Include="main.cs" >
        <Culture>fr</Culture>
    </CSFile>
</ItemGroup>
```

## <a name="see-also"></a>Zobacz także
- [Odwołanie do schematu pliku projektu](../msbuild/msbuild-project-file-schema-reference.md)
- [Elementy](../msbuild/msbuild-items.md)
