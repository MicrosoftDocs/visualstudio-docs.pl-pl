---
title: Property — element (MSBuild) | Microsoft Docs
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
ms.openlocfilehash: 99970bfbc955fe972d5e3c9a4e38ae6f57e0e0bf
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/01/2020
ms.locfileid: "75597428"
---
# <a name="property-element-msbuild"></a>Property — element (MSBuild)
Zawiera nazwę i wartość właściwości zdefiniowane przez użytkownika. Każda właściwość użyta w projekcie [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] musi być określona jako element podrzędny elementu `PropertyGroup`.

 \<Project > \<właściwości >

## <a name="syntax"></a>Składnia

```xml
<Property Condition="'String A' == 'String B'">
    Property Value
</Property>
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
|[PropertyGroup](../msbuild/propertygroup-element-msbuild.md)|Element grupujący dla właściwości.|

## <a name="text-value"></a>Wartość tekstowa
 Wartość tekstowa jest opcjonalna.

 Ten tekst Określa wartość właściwości i może zawierać kod XML.

## <a name="remarks"></a>Uwagi
 Nazwy właściwości są ograniczone tylko do znaków ASCII. Wartości właściwości są przywoływane w projekcie przez umieszczenie nazwy właściwości między "`$(`" i "`)`". Na przykład `$(builddir)\classes` być rozpoznawane jako *build\classes*, jeśli właściwość `builddir` miała wartość `build`. Aby uzyskać więcej informacji na temat właściwości, zobacz [Właściwości programu MSBuild](../msbuild/msbuild-properties.md).

## <a name="example"></a>Przykład
 Poniższy kod ustawia właściwość `Optimization` na `false` i Właściwość `DefaultVersion` na `1.0`, jeśli właściwość `Version` jest pusta.

```xml
<PropertyGroup>
    <Optimization>false</Optimization>
    <DefaultVersion Condition="'$(Version)' == ''" >1.0</DefaultVersion>
</PropertyGroup>
```

## <a name="see-also"></a>Zobacz także
- [Właściwości programu MSBuild](../msbuild/msbuild-properties.md)
- [Odwołanie do schematu pliku projektu](../msbuild/msbuild-project-file-schema-reference.md)
