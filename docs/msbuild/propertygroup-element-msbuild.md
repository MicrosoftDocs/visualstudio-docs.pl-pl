---
title: PropertyGroup Element (MSBuild) | Dokumenty firmy Microsoft
ms.date: 03/13/2017
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#PropertyGroup
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- <PropertyGroup> element [MSBuild]
- PropertyGroup element [MSBuild]
ms.assetid: ff1e6c68-b9a1-4263-a1ce-dc3b829a64d4
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: b94cf266be81b81aca9c83fe8d29b9777ee9114b
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "77632930"
---
# <a name="propertygroup-element-msbuild"></a>PropertyGroup element (MSBuild)

Zawiera zestaw elementów [właściwości](../msbuild/property-element-msbuild.md) zdefiniowanych przez użytkownika. Każdy `Property` element używany w projekcie MSBuild musi `PropertyGroup` być elementem podrzędnym elementu.

 \<> \<> PropertyGroup projektu

## <a name="syntax"></a>Składnia

```xml
<PropertyGroup Condition="'String A' == 'String B'">
    <Property1>...</Property1>
    <Property2>...</Property2>
</PropertyGroup>
```

## <a name="attributes-and-elements"></a>Atrybuty i elementy

 W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.

### <a name="attributes"></a>Atrybuty

|Atrybut|Opis|
|---------------|-----------------|
|Warunek|Atrybut opcjonalny.<br /><br /> Warunek do oceny. Aby uzyskać więcej informacji, zobacz [Warunki](../msbuild/msbuild-conditions.md).|

### <a name="child-elements"></a>Elementy podrzędne

|Element|Opis|
|-------------|-----------------|
|[Właściwość](../msbuild/property-element-msbuild.md)|Element opcjonalny.<br /><br /> Nazwa właściwości zdefiniowanej przez użytkownika, która zawiera wartość właściwości. Może istnieć zero *Property* lub więcej `PropertyGroup` Property elementów w elemencie.|

### <a name="parent-elements"></a>Elementy nadrzędne

| Element | Opis |
| - | - |
| [Project](../msbuild/project-element-msbuild.md) | Wymagany element główny pliku projektu MSBuild. |

## <a name="example"></a>Przykład

 Poniższy przykład kodu pokazuje, jak ustawić właściwości na podstawie warunku. W tym przykładzie, jeśli `CompileConfig` wartość `DEBUG`właściwości `Optimization` `Obfuscate`jest `OutputPath` , , i `PropertyGroup` właściwości wewnątrz elementu są ustawione.

```xml
<PropertyGroup Condition="'$(CompileConfig)' == 'DEBUG'" >
    <Optimization>false</Optimization>
    <Obfuscate>false</Obfuscate>
    <OutputPath>$(OutputPath)\debug</OutputPath>
</PropertyGroup>
```

## <a name="see-also"></a>Zobacz też

- [Odwołanie do schematu pliku projektu](../msbuild/msbuild-project-file-schema-reference.md)
- [Właściwości MSBuild](../msbuild/msbuild-properties.md)
