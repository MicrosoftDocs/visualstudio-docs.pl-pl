---
title: Element właściwości (MSBuild) | Dokumenty firmy Microsoft
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
ms.openlocfilehash: e50a6dd66c2dca7fa4159c578ccd334ed1d26cae
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "77632956"
---
# <a name="property-element-msbuild"></a>Element właściwości (MSBuild)

Zawiera nazwę i wartość właściwości zdefiniowanej przez użytkownika. Każda właściwość używana w projekcie MSBuild musi `PropertyGroup` być określona jako element podrzędny elementu.

 \<> \<> PropertyGroup projektu

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
|`Condition`|Atrybut opcjonalny.<br /><br /> Warunek do oceny. Aby uzyskać więcej informacji, zobacz [Warunki](../msbuild/msbuild-conditions.md).|

### <a name="child-elements"></a>Elementy podrzędne

 Brak.

### <a name="parent-elements"></a>Elementy nadrzędne

|Element|Opis|
|-------------|-----------------|
|[Propertygroup](../msbuild/propertygroup-element-msbuild.md)|Element grupowania właściwości.|

## <a name="text-value"></a>Wartość tekstowa

 Wartość tekstowa jest opcjonalna.

 Ten tekst określa wartość właściwości i może zawierać kod XML.

## <a name="remarks"></a>Uwagi

 Nazwy właściwości są ograniczone tylko do znaków ASCII. Wartości właściwości są odwoływane w projekcie, umieszczając`$(`nazwę`)`właściwości między " " i " ".Property values are referenceed in the project by placing the property name between " " and " ". Na przykład `$(builddir)\classes` można rozwiązać *build\classes* `builddir` , jeśli `build`właściwość miała wartość . Aby uzyskać więcej informacji na temat właściwości, zobacz [MSBuild właściwości](../msbuild/msbuild-properties.md).

## <a name="example"></a>Przykład

 Poniższy kod `Optimization` ustawia `false` właściwość `DefaultVersion` i `1.0` właściwość, jeśli właściwość jest pusta. `Version`

```xml
<PropertyGroup>
    <Optimization>false</Optimization>
    <DefaultVersion Condition="'$(Version)' == ''" >1.0</DefaultVersion>
</PropertyGroup>
```

## <a name="see-also"></a>Zobacz też

- [Właściwości MSBuild](../msbuild/msbuild-properties.md)
- [Odwołanie do schematu pliku projektu](../msbuild/msbuild-project-file-schema-reference.md)
