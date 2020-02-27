---
title: Property — element (MSBuild) | Microsoft Docs
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
ms.sourcegitcommit: 96737c54162f5fd5c97adef9b2d86ccc660b2135
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/26/2020
ms.locfileid: "77632930"
---
# <a name="propertygroup-element-msbuild"></a>Property — element (MSBuild)

Zawiera zestaw elementów [Właściwości](../msbuild/property-element-msbuild.md) zdefiniowanych przez użytkownika. Każdy element `Property` używany w projekcie programu MSBuild musi być elementem podrzędnym elementu `PropertyGroup`.

 \<Project > \<właściwości >

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
|Warunek|Atrybut opcjonalny.<br /><br /> Warunek do obliczenia. Aby uzyskać więcej informacji, zobacz [warunki](../msbuild/msbuild-conditions.md).|

### <a name="child-elements"></a>Elementy podrzędne

|Element|Opis|
|-------------|-----------------|
|[Właściwość](../msbuild/property-element-msbuild.md)|Element opcjonalny.<br /><br /> Nazwa właściwości zdefiniowanej przez użytkownika, która zawiera wartość właściwości. Element `PropertyGroup` może mieć zero lub więcej elementów *Właściwości* .|

### <a name="parent-elements"></a>Elementy nadrzędne

| Element | Opis |
| - | - |
| [Projektu](../msbuild/project-element-msbuild.md) | Wymagany element główny pliku projektu MSBuild. |

## <a name="example"></a>Przykład

 Poniższy przykład kodu pokazuje, jak ustawić właściwości na podstawie warunku. W tym przykładzie, jeśli wartość właściwości `CompileConfig` jest `DEBUG`, zostaną ustawione właściwości `Optimization`, `Obfuscate`i `OutputPath` wewnątrz elementu `PropertyGroup`.

```xml
<PropertyGroup Condition="'$(CompileConfig)' == 'DEBUG'" >
    <Optimization>false</Optimization>
    <Obfuscate>false</Obfuscate>
    <OutputPath>$(OutputPath)\debug</OutputPath>
</PropertyGroup>
```

## <a name="see-also"></a>Zobacz też

- [Odwołanie do schematu pliku projektu](../msbuild/msbuild-project-file-schema-reference.md)
- [Właściwości programu MSBuild](../msbuild/msbuild-properties.md)
