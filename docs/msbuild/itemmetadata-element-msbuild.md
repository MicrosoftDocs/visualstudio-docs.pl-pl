---
title: Itemmetadata — Element (MSBuild) | Dokumentacja firmy Microsoft
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
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 78be9b906efd9720d9bc7ccdbe09614899ef6818
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/25/2019
ms.locfileid: "54989591"
---
# <a name="itemmetadata-element-msbuild"></a>Itemmetadata — element (MSBuild)
Zawiera klucz metadanych zdefiniowanych przez użytkownika elementu, który zawiera wartość metadanych elementu. Element może mieć dowolną liczbę par klucz wartość metadanych.  

 \<Project>  
 \<ItemGroup>  
 \<Element >  

## <a name="syntax"></a>Składnia  

```xml  
<ItemMetadataName> Item Metadata value</ItemMetadataName>  
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
|[Element](../msbuild/item-element-msbuild.md)|Element zdefiniowany przez użytkownika, który definiuje dane wejściowe dla procesu kompilacji.|  

## <a name="text-value"></a>Wartość tekstowa  
 Wartość tekstowa jest opcjonalna.  

 Ten tekst Określa wartość elementu metadanych, które mogą być tekstem lub XML.  

## <a name="example"></a>Przykład  
 W poniższym przykładzie kodu przedstawiono sposób dodawania `Culture` metadanych z wartością `fr` do elementu `CSFile`.  

```xml  
<ItemGroup>  
    <CSFile Include="main.cs" >  
        <Culture>fr</Culture>  
    </CSFile>  
</ItemGroup>  
```  

## <a name="see-also"></a>Zobacz także  
 [Odwołanie do schematu pliku projektu](../msbuild/msbuild-project-file-schema-reference.md)   
 [Elementy](../msbuild/msbuild-items.md)
