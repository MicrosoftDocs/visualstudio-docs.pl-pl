---
title: Itemgroup — Element (MSBuild) | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
ms.topic: conceptual
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#ItemGroup
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- ItemGroup element [MSBuild]
- <ItemGroup> element [MSBuild]
ms.assetid: aac894e3-a9f1-4bbc-a796-6ef07001f35b
caps.latest.revision: 27
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 18d01e5ebe9b1f675fb0af8b2bf5737cf4ab9f78
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54772082"
---
# <a name="itemgroup-element-msbuild"></a>ItemGroup — Element (MSBuild)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
Zawiera zestaw zdefiniowanych przez użytkownika [elementu](../msbuild/item-element-msbuild.md) elementów. Każdy element używany w [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] projekt musi być określony jako element podrzędny elementu `ItemGroup` elementu.  
  
 \<Project>  
 \<ItemGroup>  
  
## <a name="syntax"></a>Składnia  
  
```  
<ItemGroup Condition="'String A' == 'String B'">  
    <Item1>... </Item1>  
    <Item2>... </Item2>  
</ItemGroup>  
```  
  
## <a name="attributes-and-elements"></a>Atrybuty i elementy  
 W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.  
  
### <a name="attributes"></a>Atrybuty  
  
|Atrybut|Opis|  
|---------------|-----------------|  
|`Condition`|Atrybut opcjonalny. Warunek, który ma zostać obliczone. Aby uzyskać więcej informacji, zobacz [warunki](../msbuild/msbuild-conditions.md).|  
  
### <a name="child-elements"></a>Elementy podrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[Element](../msbuild/item-element-msbuild.md)|Definiuje dane wejściowe dla procesu kompilacji. Może wynosić zero lub więcej `Item` elementów w `ItemGroup`.|  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[Project](../msbuild/project-element-msbuild.md)|Element główny wymagany [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] pliku projektu.|  
|[Docelowy](../msbuild/target-element-msbuild.md)|Począwszy od programu .NET Framework 3.5, `ItemGroup` element może znajdować się wewnątrz `Target` elementu. Aby uzyskać więcej informacji, zobacz [cele](../msbuild/msbuild-targets.md).|  
  
## <a name="remarks"></a>Uwagi  
  
## <a name="example"></a>Przykład  
 Poniższy przykład kodu pokazuje kolekcji elementów zdefiniowanych przez użytkownika `Res` i `CodeFiles` zadeklarowane wewnątrz `ItemGroup` elementu. Każdy z elementów w `Res` elementu Kolekcja zawiera element podrzędny zdefiniowanych przez użytkownika [itemmetadata —](../msbuild/itemmetadata-element-msbuild.md) elementu.  
  
```  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
    <ItemGroup>  
        <Res Include = "Strings.fr.resources" >  
            <Culture>fr</Culture>  
        </Res>  
        <Res Include = "Dialogs.fr.resources" >  
            <Culture>fr</Culture>  
        </Res>  
  
        <CodeFiles Include="**\*.cs" Exclude="**\generated\*.cs" />  
        <CodeFiles Include="..\..\Resources\Constants.cs" />  
    </ItemGroup>  
...  
</Project>  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Odwołanie do schematu pliku projektu](../msbuild/msbuild-project-file-schema-reference.md)   
 [Elementy](../msbuild/msbuild-items.md)   
 [Wspólne elementy projektów MSBuild](../msbuild/common-msbuild-project-items.md)
