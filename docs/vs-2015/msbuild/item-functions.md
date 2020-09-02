---
title: Funkcje elementów | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
ms.topic: conceptual
helpviewer_keywords:
- msbuild, Item functions
ms.assetid: 5e6df3cc-2db8-4cbd-8fdd-3ffd03ac0876
caps.latest.revision: 32
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: c94624aaea629c087b552ee46266a44f534888d5
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "68192897"
---
# <a name="item-functions"></a>Funkcje elementów
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Począwszy od programu MSBuild 4,0, kod w zadaniach i obiektach docelowych może wywoływać funkcje elementu, aby uzyskać informacje o elementach w projekcie. Te funkcje upraszczają pobieranie elementów DISTINCT () i są szybsze niż pętle w elementach.  
  
## <a name="string-item-functions"></a>Funkcje elementu String  
 Można użyć metod i właściwości ciągu w .NET Framework, aby wykonywać operacje na dowolnej wartości elementu. Dla <xref:System.String> metod należy określić nazwę metody. Dla <xref:System.String> właściwości, należy określić nazwę właściwości po "get_".  
  
 Dla elementów, które mają wiele ciągów, Metoda ciągu lub właściwość jest uruchamiana dla każdego ciągu.  
  
 Poniższy przykład pokazuje, jak używać tych funkcji ciągów znaków.  
  
```  
<ItemGroup>  
    <theItem Include="andromeda;tadpole;cartwheel" />  
</ItemGroup>  
  
<Target Name = "go">  
    <Message Text="IndexOf  @(theItem->IndexOf('r'))" />  
    <Message Text="Replace  @(theItem->Replace('tadpole', 'pinwheel'))" />  
    <Message Text="Length   @(theItem->get_Length())" />  
    <Message Text="Chars    @(theItem->get_Chars(2))" />  
</Target>  
  
  <!--  
  Output:  
    IndexOf  3;-1;2  
    Replace  andromeda;pinwheel;cartwheel  
    Length   9;7;9  
    Chars    d;d;r  
  -->  
```  
  
## <a name="intrinsic-item-functions"></a>Funkcje elementu wewnętrznego  
 W poniższej tabeli wymieniono funkcje wewnętrzne dostępne dla elementów.  
  
|Funkcja|Przykład|Opis|  
|--------------|-------------|-----------------|  
|`Count`|`@(MyItem->Count())`|Zwraca liczbę elementów.|  
|`DirectoryName`|`@(MyItem->DirectoryName())`|Zwraca odpowiednik `Path.DirectoryName` dla każdego elementu.|  
|`Distinct`|`@(MyItem->Distinct())`|Zwraca elementy, które mają różne `Include` wartości. Metadane zostały zignorowane. W porównaniu jest rozróżniana wielkość liter.|  
|`DistinctWithCase`|`@(MyItem->DistinctWithCase())`|Zwraca elementy, które mają różne `itemspec` wartości. Metadane zostały zignorowane. W porównaniu z rozróżnianiem wielkości liter.|  
|`Reverse`|`@(MyItem->Reverse())`|Zwraca elementy w kolejności odwrotnej.|  
|`AnyHaveMetadataValue`|`@(MyItem->AnyHaveMetadataValue("MetadataName", "MetadataValue"))`|Zwraca wartość, `boolean` Aby wskazać, czy dowolny element ma daną nazwę metadanych, i jego wartości. W porównaniu jest rozróżniana wielkość liter.|  
|`ClearMetadata`|`@(MyItem->ClearMetadata())`|Zwraca elementy z wyczyszczonymi metadanymi. Tylko `itemspec` jest zachowywane.|  
|`HasMetadata`|`@(MyItem->HasMetadataValue("MetadataName")`|Zwraca elementy, które mają daną nazwę metadanych. W porównaniu jest rozróżniana wielkość liter.|  
|`Metadata`|`@(MyItem->Metadata("MetadataName"))`|Zwraca wartości metadanych, które mają nazwę metadanych.|  
|`WithMetadataValue`|`@(MyItem->WithMetadataValue("MetadataName", "MetadataValue")`|Zwraca elementy, które mają daną nazwę i wartość metadanych. W porównaniu jest rozróżniana wielkość liter.|  
  
 Poniższy przykład pokazuje, jak używać funkcji elementu wewnętrznego.  
  
```  
<ItemGroup>  
    <TheItem Include="first">  
        <Plant>geranium</Plant>  
    </TheItem>  
    <TheItem Include="second">  
        <Plant>algae</Plant>  
    </TheItem>  
    <TheItem Include="third">  
        <Plant>geranium</Plant>  
    </TheItem>  
</ItemGroup>  
  
<Target Name="go">  
    <Message Text="MetaData:    @(TheItem->Metadata('Plant'))" />  
    <Message Text="HasMetadata: @(theItem->HasMetadata('Plant'))" />  
    <Message Text="WithMetadataValue: @(TheItem->WithMetadataValue('Plant', 'geranium'))" />  
    <Message Text=" " />  
    <Message Text="Count:   @(theItem->Count())" />  
    <Message Text="Reverse: @(theItem->Reverse())" />  
</Target>  
  
  <!--   
  Output:  
    MetaData:    geranium;algae;geranium  
    HasMetadata: first;second;third  
    WithMetadataValue: first;third  
  
    Count:   3  
    Reverse: third;second;first  
  -->  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Elementy](../msbuild/msbuild-items.md)
