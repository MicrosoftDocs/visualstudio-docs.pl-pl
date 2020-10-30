---
title: Property — element (MSBuild) | Microsoft Docs
description: Dowiedz się więcej o elemencie właściwości programu MSBuild, który zawiera zdefiniowaną przez użytkownika nazwę właściwości i wartość, która musi być określona jako element podrzędny elementu właściwości.
ms.custom: SEO-VS-2020
ms.date: 03/13/2017
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- <Property> Element [MSBuild]
- Property Element [MSBuild]
ms.assetid: 69ab08ab-3e76-41dd-a01b-49aa1d2e0cac
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 8c17906467579e8fc532372371df8be76b40e7f0
ms.sourcegitcommit: 1a36533f385e50c05f661f440380fda6386ed3c1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2020
ms.locfileid: "93048836"
---
# <a name="property-element-msbuild"></a>Property — element (MSBuild)

Zawiera nazwę i wartość właściwości zdefiniowane przez użytkownika. Każda właściwość użyta w projekcie programu MSBuild musi być określona jako element podrzędny `PropertyGroup` elementu.

 \<Project> \<PropertyGroup>

## <a name="syntax"></a>Składnia

```xml
<Property Condition="'String A' == 'String B'">
    Property Value
</Property>
```

## <a name="attributes-and-elements"></a>Atrybuty i elementy

 W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.

### <a name="attributes"></a>Atrybuty

|Atrybut|Opis|
|---------------|-----------------|
|`Condition`|Atrybut opcjonalny.<br /><br /> Warunek do obliczenia. Aby uzyskać więcej informacji, zobacz [warunki](../msbuild/msbuild-conditions.md).|

### <a name="child-elements"></a>Elementy podrzędne

 Brak.

### <a name="parent-elements"></a>Elementy nadrzędne

|Element|Opis|
|-------------|-----------------|
|[PropertyGroup](../msbuild/propertygroup-element-msbuild.md)|Element grupujący dla właściwości.|

## <a name="text-value"></a>Wartość tekstowa

 Wartość tekstowa jest opcjonalna.

 Ten tekst Określa wartość właściwości i może zawierać kod XML.

## <a name="remarks"></a>Uwagi

 Nazwy właściwości są ograniczone tylko do znaków ASCII. Wartości właściwości są przywoływane w projekcie przez umieszczenie nazwy właściwości między " `$(` " i " `)` ". Na przykład `$(builddir)\classes` rozwiązanie to *build\classes* , jeśli `builddir` Właściwość miała wartość `build` . Aby uzyskać więcej informacji na temat właściwości, zobacz [Właściwości programu MSBuild](../msbuild/msbuild-properties.md).

## <a name="example"></a>Przykład

 Poniższy kod ustawia `Optimization` Właściwość na `false` i `DefaultVersion` Właściwość na, `1.0` Jeśli `Version` Właściwość jest pusta.

```xml
<PropertyGroup>
    <Optimization>false</Optimization>
    <DefaultVersion Condition="'$(Version)' == ''" >1.0</DefaultVersion>
</PropertyGroup>
```

## <a name="see-also"></a>Zobacz też

- [właściwości programu MSBuild](../msbuild/msbuild-properties.md)
- [Odwołanie do schematu pliku projektu](../msbuild/msbuild-project-file-schema-reference.md)
