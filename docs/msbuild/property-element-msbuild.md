---
title: Property — Element (MSBuild) | Dokumentacja firmy Microsoft
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
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 739e39bd09e8387904570d3690e7c9ff1447fae3
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/02/2019
ms.locfileid: "53864446"
---
# <a name="property-element-msbuild"></a>Property — element (MSBuild)
Zawiera użytkownika zdefiniowane nazwy i wartości właściwości. Dla każdej właściwości używana w [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] projekt musi być określony jako element podrzędny elementu `PropertyGroup` elementu.  

 \<Project>  
 \<PropertyGroup>  

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
|`Condition`|Atrybut opcjonalny.<br /><br /> Warunek, który ma zostać obliczone. Aby uzyskać więcej informacji, zobacz [warunki](../msbuild/msbuild-conditions.md).|  

### <a name="child-elements"></a>Elementy podrzędne  
 Brak.  

### <a name="parent-elements"></a>Elementy nadrzędne  

|Element|Opis|  
|-------------|-----------------|  
|[PropertyGroup](../msbuild/propertygroup-element-msbuild.md)|Element grupujący właściwości.|  

## <a name="text-value"></a>Wartość tekstowa  
 Wartość tekstowa jest opcjonalna.  

 Ten tekst Określa wartość właściwości i może zawierać kod XML.  

## <a name="remarks"></a>Uwagi  
 Nazwy właściwości są ograniczone do tylko znaki ASCII. Wartości właściwości są przywoływane w projekcie, umieszczając nazwę właściwości między "`$(`"i"`)`". Na przykład `$(builddir)\classes` może prowadzić do *build\classes*, jeśli `builddir` właściwość ma wartość `build`. Aby uzyskać więcej informacji na temat właściwości, zobacz [właściwości programu MSBuild](../msbuild/msbuild-properties.md).  

## <a name="example"></a>Przykład  
 Poniższy kod ustawia `Optimization` właściwości `false` i `DefaultVersion` właściwości `1.0` Jeśli `Version` właściwość jest pusta.  

```xml  
<PropertyGroup>  
    <Optimization>false</Optimization>  
    <DefaultVersion Condition="'$(Version)' == ''" >1.0</DefaultVersion>  
</PropertyGroup>  
```  

## <a name="see-also"></a>Zobacz także
[Właściwości programu MSBuild](../msbuild/msbuild-properties.md)  
 [Odwołanie do schematu pliku projektu](../msbuild/msbuild-project-file-schema-reference.md)
