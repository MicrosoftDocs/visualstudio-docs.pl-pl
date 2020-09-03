---
title: Property — element (MSBuild) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
ms.topic: conceptual
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
caps.latest.revision: 24
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 6590464b78d6b5452ce266d701aefc0f739185b3
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "68155947"
---
# <a name="propertygroup-element-msbuild"></a>PropertyGroup — Element (MSBuild)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Zawiera zestaw elementów [Właściwości](../msbuild/property-element-msbuild.md) zdefiniowanych przez użytkownika. Każdy `Property` element użyty w [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] projekcie musi być elementem podrzędnym `PropertyGroup` elementu.  
  
 \<Project>  
 \<PropertyGroup>  
  
## <a name="syntax"></a>Składnia  
  
```  
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
|[Właściwość](../msbuild/property-element-msbuild.md)|Element opcjonalny.<br /><br /> Nazwa właściwości zdefiniowanej przez użytkownika, która zawiera wartość właściwości. Element może mieć zero lub więcej elementów *Właściwości* `PropertyGroup` .|  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[Project](../msbuild/project-element-msbuild.md)|Wymagany element główny [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] pliku projektu.|  
  
## <a name="example"></a>Przykład  
 Poniższy przykład kodu pokazuje, jak ustawić właściwości na podstawie warunku. W tym przykładzie, jeśli wartość `CompileConfig` Właściwości to `DEBUG` , `Optimization` `Obfuscate` właściwości, i `OutputPath` wewnątrz `PropertyGroup` elementu są ustawione.  
  
```  
<PropertyGroup Condition="'$(CompileConfig)' == 'DEBUG'" >  
    <Optimization>false</Optimization>  
    <Obfuscate>false</Obfuscate>  
    <OutputPath>$(OutputPath)\debug</OutputPath>  
</PropertyGroup>  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Odwołanie do schematu pliku projektu](../msbuild/msbuild-project-file-schema-reference.md)  
 [Właściwości programu MSBuild](msbuild-properties1.md)
