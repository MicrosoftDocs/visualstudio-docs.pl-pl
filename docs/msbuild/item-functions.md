---
title: Funkcje zapasów | Dokumenty firmy Microsoft
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
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "77633684"
---
# <a name="item-functions"></a>Funkcje elementów

Kod w zadaniach i obiektów docelowych można wywołać funkcje elementu, aby uzyskać informacje o elementach w projekcie (w MSBuild 4.0 i nowsze). Te funkcje upraszczają uzyskiwanie różnych elementów i są szybsze niż zapętlanie elementów.

## <a name="string-item-functions"></a>Funkcje elementów ciągu

Można użyć metody ciągu i właściwości w programie .NET Framework do działania na dowolnej wartości elementu. W <xref:System.String> przypadku metod określ nazwę metody. W <xref:System.String> przypadku właściwości należy określić nazwę właściwości po "get_".

Dla elementów, które mają wiele ciągów, metoda ciągu lub właściwość działa na każdym ciągu.

W poniższym przykładzie pokazano, jak używać tych funkcji elementu ciągu.

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

## <a name="intrinsic-item-functions"></a>Wewnętrzne funkcje elementu

W poniższej tabeli wymieniono wewnętrzne funkcje dostępne dla elementów.

|Funkcja|Przykład|Opis|
|--------------|-------------|-----------------|
|`Count`|`@(MyItem->Count())`|Zwraca liczbę towarów.|
|`DirectoryName`|`@(MyItem->DirectoryName())`|Zwraca odpowiednik `Path.DirectoryName` dla każdego towaru.|
|`Distinct`|`@(MyItem->Distinct())`|Zwraca elementy, `Include` które mają różne wartości. Metadane są ignorowane. Porównanie jest niewrażliwe na przypadek.|
|`DistinctWithCase`|`@(MyItem->DistinctWithCase())`|Zwraca elementy, `itemspec` które mają różne wartości. Metadane są ignorowane. W porównaniu jest rozróżniana wielkość liter.|
|`Reverse`|`@(MyItem->Reverse())`|Zwraca zapasy w odwrotnej kolejności.|
|`AnyHaveMetadataValue`|`@(MyItem->AnyHaveMetadataValue("MetadataName", "MetadataValue"))`|Zwraca `boolean` a, aby wskazać, czy dowolny element ma podana nazwa metadanych i wartość. Porównanie jest niewrażliwe na przypadek.|
|`ClearMetadata`|`@(MyItem->ClearMetadata())`|Zwraca elementy z wyczyszczonymi metadanymi. Tylko `itemspec` jest zachowana.|
|`HasMetadata`|`@(MyItem->HasMetadata("MetadataName"))`|Zwraca elementy, które mają podana nazwa metadanych. Porównanie jest niewrażliwe na przypadek.|
|`Metadata`|`@(MyItem->Metadata("MetadataName"))`|Zwraca wartości metadanych, które mają nazwę metadanych.|
|`WithMetadataValue`|`@(MyItem->WithMetadataValue("MetadataName", "MetadataValue"))`|Zwraca elementy, które mają podana nazwa i wartość metadanych. Porównanie jest niewrażliwe na przypadek.|

W poniższym przykładzie pokazano, jak używać wewnętrznych funkcji elementu.

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

- [Items](../msbuild/msbuild-items.md)
