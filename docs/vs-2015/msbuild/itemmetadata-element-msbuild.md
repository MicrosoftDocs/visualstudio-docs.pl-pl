---
title: Itemmetadata — Element (MSBuild) | Dokumentacja firmy Microsoft
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
- ItemMetadata Element [MSBuild]
- <ItemMetadata> Element [MSBuild]
ms.assetid: e3db5122-202d-43a9-b2f4-3e0ec4ed3d08
caps.latest.revision: 20
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 8e3d9f72abfd095288b50ab8de9b9bc3eae4cc51
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "68162368"
---
# <a name="itemmetadata-element-msbuild"></a>ItemMetadata — Element (MSBuild)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Zawiera klucz metadanych zdefiniowanych przez użytkownika elementu, który zawiera wartość metadanych elementu. Element może mieć dowolną liczbę par klucz wartość metadanych.  
  
 \<Project>  
 \<ItemGroup>  
 \<Element >  
  
## <a name="syntax"></a>Składnia  
  
```  
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
  
## <a name="remarks"></a>Uwagi  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie kodu przedstawiono sposób dodawania `Culture` metadanych z wartością `fr` do elementu `CSFile`.  
  
```  
<ItemGroup>  
    <CSFile Include="main.cs" >  
        <Culture>fr</Culture>  
    </CSFile>  
</ItemGroup>  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Odwołanie do schematu pliku projektu](../msbuild/msbuild-project-file-schema-reference.md)   
 [Elementy](../msbuild/msbuild-items.md)
