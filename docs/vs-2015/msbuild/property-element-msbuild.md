---
title: Property — element (MSBuild) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- <Property> Element [MSBuild]
- Property Element [MSBuild]
ms.assetid: 69ab08ab-3e76-41dd-a01b-49aa1d2e0cac
caps.latest.revision: 20
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: eefe0160328f1eb6b3fe841742547efe8be50ec1
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "68158277"
---
# <a name="property-element-msbuild"></a>Property — Element (MSBuild)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Zawiera nazwę i wartość właściwości zdefiniowane przez użytkownika. Każda właściwość użyta w [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] projekcie musi być określona jako element podrzędny `PropertyGroup` elementu.  
  
 \<Project>  
 \<PropertyGroup>  
  
## <a name="syntax"></a>Składnia  
  
```  
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
 Nazwy właściwości są ograniczone tylko do znaków ASCII. Wartości właściwości są przywoływane w projekcie przez umieszczenie nazwy właściwości między " `$(` " i " `)` ". Na przykład, `$(builddir)\classes` Jeśli właściwość ma wartość, zostanie rozpoznany jako "build\classes" `builddir` `build` . Aby uzyskać więcej informacji na temat właściwości, zobacz [Właściwości programu MSBuild](msbuild-properties1.md).  
  
## <a name="example"></a>Przykład  
 Poniższy kod ustawia `Optimization` Właściwość na `false` i `DefaultVersion` Właściwość na, `1.0` Jeśli `Version` Właściwość jest pusta.  
  
```  
<PropertyGroup>  
    <Optimization>false</Optimization>  
    <DefaultVersion Condition="'$(Version)' == ''" >1.0</DefaultVersion>  
</PropertyGroup>  
```  
  
## <a name="see-also"></a>Zobacz też
[Właściwości programu MSBuild](msbuild-properties1.md)  
 [Odwołanie do schematu pliku projektu](../msbuild/msbuild-project-file-schema-reference.md)
