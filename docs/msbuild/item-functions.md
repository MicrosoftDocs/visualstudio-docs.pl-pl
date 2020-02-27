---
title: Funkcje elementów | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- msbuild, Item functions
ms.assetid: 5e6df3cc-2db8-4cbd-8fdd-3ffd03ac0876
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: af4fb872206611ea5eb1aa93b7aa759615b56e41
ms.sourcegitcommit: 96737c54162f5fd5c97adef9b2d86ccc660b2135
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/26/2020
ms.locfileid: "77633684"
---
# <a name="item-functions"></a>Funkcje elementów

Kod w zadaniach i obiektach docelowych może wywoływać funkcje elementu, aby uzyskać informacje o elementach w projekcie (w programie MSBuild 4,0 i nowszych). Te funkcje upraszczają pobieranie odrębnych elementów i są szybsze niż pętle w elementach.

## <a name="string-item-functions"></a>Funkcje elementu String

Można użyć metod i właściwości ciągu w .NET Framework, aby wykonywać operacje na dowolnej wartości elementu. W przypadku metod <xref:System.String> należy określić nazwę metody. Dla właściwości <xref:System.String> Określ nazwę właściwości po "get_".

Dla elementów, które mają wiele ciągów, Metoda ciągu lub właściwość jest uruchamiana dla każdego ciągu.

Poniższy przykład pokazuje, jak używać tych funkcji ciągów znaków.

```xml
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
|`Distinct`|`@(MyItem->Distinct())`|Zwraca elementy, które mają unikatowe `Include` wartości. Metadane zostały zignorowane. W porównaniu jest rozróżniana wielkość liter.|
|`DistinctWithCase`|`@(MyItem->DistinctWithCase())`|Zwraca elementy, które mają unikatowe `itemspec` wartości. Metadane zostały zignorowane. W porównaniu z rozróżnianiem wielkości liter.|
|`Reverse`|`@(MyItem->Reverse())`|Zwraca elementy w kolejności odwrotnej.|
|`AnyHaveMetadataValue`|`@(MyItem->AnyHaveMetadataValue("MetadataName", "MetadataValue"))`|Zwraca `boolean`, aby wskazać, czy każdy element ma daną nazwę i wartość metadanych. W porównaniu jest rozróżniana wielkość liter.|
|`ClearMetadata`|`@(MyItem->ClearMetadata())`|Zwraca elementy z wyczyszczonymi metadanymi. Tylko `itemspec` są zachowywane.|
|`HasMetadata`|`@(MyItem->HasMetadata("MetadataName"))`|Zwraca elementy, które mają daną nazwę metadanych. W porównaniu jest rozróżniana wielkość liter.|
|`Metadata`|`@(MyItem->Metadata("MetadataName"))`|Zwraca wartości metadanych, które mają nazwę metadanych.|
|`WithMetadataValue`|`@(MyItem->WithMetadataValue("MetadataName", "MetadataValue"))`|Zwraca elementy, które mają daną nazwę i wartość metadanych. W porównaniu jest rozróżniana wielkość liter.|

Poniższy przykład pokazuje, jak używać funkcji elementu wewnętrznego.

```xml
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

- [Elementy](../msbuild/msbuild-items.md)
