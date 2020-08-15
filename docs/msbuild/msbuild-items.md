---
title: Elementy MSBuild | Microsoft Docs
description: Użyj atrybutu dołączania MSBuild elementu Item, aby określić pliki do uwzględnienia w kompilacji
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- MSBuild, Items
ms.assetid: d762eff4-c92a-4b5f-a944-1ca30aa22319
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 020983182706bd6d9382f4d0bd4885ffa0f86f52
ms.sourcegitcommit: 577c905de52057a741e68c2ed168ea527813fda5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/15/2020
ms.locfileid: "88247584"
---
# <a name="msbuild-items"></a>Elementy programu MSBuild

Elementy programu MSBuild są wejściami do systemu kompilacji i zazwyczaj reprezentują pliki (pliki są określone w `Include` atrybucie). Elementy są pogrupowane w typy elementów na podstawie ich nazw elementów. Typy elementów są nazwanymi elementami, które mogą być używane jako parametry zadań. Zadania używają wartości elementów do wykonania kroków procesu kompilacji.

 Ponieważ elementy są nazwane przez typ elementu, do którego należą, można użyć zamiennie warunków "Item" i "value Item".

## <a name="create-items-in-a-project-file"></a>Tworzenie elementów w pliku projektu

 Elementy w pliku projektu deklaruje się jako elementy podrzędne elementu [Item](../msbuild/itemgroup-element-msbuild.md) . Nazwa elementu podrzędnego jest typem elementu. `Include`Atrybut elementu określa elementy (pliki), które mają być dołączone do tego typu elementu. Na przykład poniższy kod XML tworzy typ elementu o nazwie `Compile` , który zawiera dwa pliki.

```xml
<ItemGroup>
    <Compile Include = "file1.cs"/>
    <Compile Include = "file2.cs"/>
</ItemGroup>
```

 Element *file2.cs* nie zastępuje elementu *file1.cs*; Zamiast tego nazwa pliku jest dołączana do listy wartości `Compile` typu elementu.

 Poniższy kod XML tworzy ten sam typ elementu przez zadeklarowanie obu plików w jednym `Include` atrybucie. Należy zauważyć, że nazwy plików są oddzielone średnikami.

```xml
<ItemGroup>
    <Compile Include = "file1.cs;file2.cs"/>
</ItemGroup>
```

`Include`Atrybut jest ścieżką interpretowaną względem folderu pliku projektu, $ (MSBuildProjectPath), nawet jeśli element znajduje się w zaimportowanym pliku, takim jak plik *. targets* .

## <a name="create-items-during-execution"></a>Tworzenie elementów podczas wykonywania

 Elementy, które są poza elementami [docelowymi](../msbuild/target-element-msbuild.md) , są przypisane do wartości w fazie oceny kompilacji. Podczas kolejnej fazy wykonywania elementy mogą być tworzone lub modyfikowane w następujący sposób:

- Każde zadanie może emitować element. Aby emitować element, element [Task](../msbuild/task-element-msbuild.md) musi mieć podrzędny element [wyjściowy](../msbuild/output-element-msbuild.md) , który ma `ItemName` atrybut.

- Zadanie [elementu "Item](../msbuild/createitem-task.md) " może emitować element. Takie użycie jest przestarzałe.

- Począwszy od .NET Framework 3,5, `Target` elementy mogą zawierać elementy elementu [Item](../msbuild/itemgroup-element-msbuild.md) , które mogą zawierać elementy Item.

## <a name="reference-items-in-a-project-file"></a>Elementy referencyjne w pliku projektu

 Aby odwołać się do typów elementów w całym pliku projektu, należy użyć składni @ ( \<ItemType> ). Na przykład, można odwołać się do typu elementu w poprzednim przykładzie przy użyciu `@(Compile)` . Za pomocą tej składni można przekazać elementy do zadań, określając typ elementu jako parametr tego zadania. Aby uzyskać więcej informacji, zobacz [jak: Wybieranie plików do skompilowania](../msbuild/how-to-select-the-files-to-build.md).

 Domyślnie elementy typu elementu są oddzielone średnikami (;) po jego rozszerzeniu. \<ItemType>Aby określić separator inny niż domyślny, można użyć składni @ (, ' \<separator> '). Aby uzyskać więcej informacji, zobacz [jak: wyświetlić listę elementów rozdzieloną przecinkami](../msbuild/how-to-display-an-item-list-separated-with-commas.md).

## <a name="use-wildcards-to-specify-items"></a>Użyj symboli wieloznacznych, aby określić elementy

Możesz użyć `**` `*` `?` symboli wieloznacznych, aby określić grupę plików jako dane wejściowe dla kompilacji, a nie osobno wymieniać każdy plik.

- `?`Symbol wieloznaczny dopasowuje pojedynczy znak.
- `*`Symbol wieloznaczny dopasowuje zero lub więcej znaków.
- `**`Sekwencja znaków wieloznacznych jest zgodna ze ścieżką częściową.

Na przykład można określić wszystkie `.cs` pliki w katalogu, który zawiera plik projektu, przy użyciu następującego elementu w pliku projektu.

```xml
<CSFile Include="*.cs"/>
```

Następujący element wybiera wszystkie `.vb` pliki na `D:` dysku:

```xml
<VBFile Include="D:/**/*.vb"/>
```

Jeśli chcesz dołączyć literał `*` lub `?` znaki do elementu bez rozwinięcia symboli wieloznacznych, musisz [wprowadzić symbole wieloznaczne](../msbuild/how-to-escape-special-characters-in-msbuild.md).

Aby uzyskać więcej informacji na temat symboli wieloznacznych, zobacz [How to: Wybierz pliki do skompilowania](../msbuild/how-to-select-the-files-to-build.md).

## <a name="use-the-exclude-attribute"></a>Użyj atrybutu Exclude

 Elementy elementu mogą zawierać `Exclude` atrybut, który wyklucza określone elementy (pliki) z typu elementu. Ten `Exclude` atrybut jest zwykle używany razem z symbolami wieloznacznymi. Na przykład poniższy kod XML dodaje każdy plik *CS* w katalogu do typu elementu CSFile, z wyjątkiem pliku *DoNotBuild.cs* .

```xml
<ItemGroup>
    <CSFile  Include="*.cs"  Exclude="DoNotBuild.cs"/>
</ItemGroup>
```

 Ten `Exclude` atrybut ma wpływ tylko na elementy, które są dodawane przez `Include` atrybut w elemencie elementu, który zawiera te wartości. W poniższym przykładzie nie można wykluczyć pliku *Form1.cs*, który został dodany w poprzednim elemencie elementu.

```xml
<Compile Include="*.cs" />
<Compile Include="*.res" Exclude="Form1.cs">
```

 Aby uzyskać więcej informacji, zobacz [jak: wykluczanie plików z kompilacji](../msbuild/how-to-exclude-files-from-the-build.md).

## <a name="item-metadata"></a>Metadane elementu

 Elementy mogą zawierać metadane oprócz informacji w `Include` `Exclude` atrybutach i. Te metadane mogą służyć do zadań, które wymagają więcej informacji na temat elementów lub zadań wsadowych i elementów docelowych. Aby uzyskać więcej informacji, zobacz Tworzenie [pakietów wsadowych](../msbuild/msbuild-batching.md).

 Metadata jest kolekcją par klucz-wartość, które są zadeklarowane w pliku projektu jako elementy podrzędne elementu elementu. Nazwa elementu podrzędnego jest nazwą metadanych, a wartością elementu podrzędnego jest wartość metadanych.

 Metadane są skojarzone z elementem elementu, który go zawiera. Na przykład poniższy kod XML dodaje `Culture` metadane, które mają wartość `Fr` zarówno *one.cs* , jak i *Two.cs* elementów typu CSFile.

```xml
<ItemGroup>
    <CSFile Include="one.cs;two.cs">
        <Culture>Fr</Culture>
    </CSFile>
</ItemGroup>
```

 Element może mieć zero lub więcej wartości metadanych. Wartości metadanych można zmienić w dowolnym momencie. Jeśli ustawisz metadane na wartość pustą, możesz skutecznie usunąć ją z kompilacji.

### <a name="reference-item-metadata-in-a-project-file"></a><a name="BKMK_ReferencingItemMetadata"></a> Metadane elementu odwołania w pliku projektu

 Metadane elementu można odwoływać w całym pliku projektu przy użyciu składni%( \<ItemMetadataName> ). Jeśli istnieje niejednoznaczność, można kwalifikować odwołanie przy użyciu nazwy typu elementu. Na przykład można określić%( \<ItemType.ItemMetaDataName> ). Poniższy przykład używa metadanych wyświetlania do wsadowego zadania wiadomości. Aby uzyskać więcej informacji o sposobach używania metadanych elementu na potrzeby tworzenia pakietów wsadowych, zobacz [metadane elementu w usłudze Batch zadania](../msbuild/item-metadata-in-task-batching.md).

```xml
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
    <ItemGroup>
        <Stuff Include="One.cs" >
            <Display>false</Display>
        </Stuff>
        <Stuff Include="Two.cs">
            <Display>true</Display>
        </Stuff>
    </ItemGroup>
    <Target Name="Batching">
        <Message Text="@(Stuff)" Condition=" '%(Display)' == 'true' "/>
    </Target>
</Project>
```

### <a name="well-known-item-metadata"></a><a name="BKMK_WellKnownItemMetadata"></a> Metadane dobrze znanego elementu

 Gdy element zostanie dodany do typu elementu, do tego elementu są przypisane pewne dobrze znane metadane. Na przykład wszystkie elementy mają dobrze znane metadane%( \<Filename> ), których wartość jest nazwą pliku elementu (bez rozszerzenia). Aby uzyskać więcej informacji, zobacz [dobrze znane metadane elementu](../msbuild/msbuild-well-known-item-metadata.md).

### <a name="transform-item-types-by-using-metadata"></a><a name="BKMK_Transforming"></a> Przekształcanie typów elementów za pomocą metadanych

 Listy elementów można przekształcać na nowe listy elementów przy użyciu metadanych. Na przykład można przekształcić typ elementu `CppFiles` zawierający elementy, które reprezentują pliki *. cpp* , do odpowiedniej listy plików *. obj* przy użyciu wyrażenia `@(CppFiles -> '%(Filename).obj')` .

 Poniższy kod tworzy `CultureResource` Typ elementu zawierający kopie wszystkich `EmbeddedResource` elementów z `Culture` metadanymi. `Culture`Wartość metadanych jest wartością nowego metadanych `CultureResource.TargetDirectory` .

```xml
<Target Name="ProcessCultureResources">
    <ItemGroup>
        <CultureResource Include="@(EmbeddedResource)"
            Condition="'%(EmbeddedResource.Culture)' != ''">
            <TargetDirectory>%(EmbeddedResource.Culture) </TargetDirectory>
        </CultureResource>
    </ItemGroup>
</Target>
```

 Aby uzyskać więcej informacji, zobacz [transformacje](../msbuild/msbuild-transforms.md).

## <a name="item-definitions"></a>Definicje elementów

 Począwszy od .NET Framework 3,5, można dodać domyślne metadane do dowolnego typu elementu przy użyciu [elementu ItemDefinitionGroup](../msbuild/itemdefinitiongroup-element-msbuild.md). Podobnie jak dobrze znane metadane, domyślne metadane są skojarzone ze wszystkimi elementami typu elementu określonego przez użytkownika. Można jawnie przesłonić domyślne metadane w definicji elementu. Na przykład poniższy kod XML daje `Compile` elementy *one.cs* i *Three.cs* metadane `BuildDay` z wartością "poniedziałek". Kod nadaje elementowi *Two.cs* metadane `BuildDay` z wartością "wtorek".

```xml
<ItemDefinitionGroup>
    <Compile>
        <BuildDay>Monday</BuildDay>
    </Compile>
</ItemDefinitionGroup>
<ItemGroup>
    <Compile Include="one.cs;three.cs" />
    <Compile Include="two.cs">
        <BuildDay>Tuesday</BuildDay>
    </Compile>
</ItemGroup>
```

 Aby uzyskać więcej informacji, zobacz [definicje elementu](../msbuild/item-definitions.md).

## <a name="attributes-for-items-in-an-itemgroup-of-a-target"></a>Atrybuty elementów w elemencie Items elementu docelowego

 Począwszy od .NET Framework 3,5, `Target` elementy mogą zawierać elementy elementu [Item](../msbuild/itemgroup-element-msbuild.md) , które mogą zawierać elementy Item. Atrybuty w tej sekcji są prawidłowe, jeśli są określone dla elementu w elemencie `ItemGroup` `Target` .

### <a name="remove-attribute"></a><a name="BKMK_RemoveAttribute"></a> Usuń atrybut

 Ten `Remove` atrybut usuwa określone elementy (pliki) z typu elementu. Ten atrybut został wprowadzony w .NET Framework 3,5 (tylko wewnątrz elementów docelowych). W programie MSBuild 15,0 obsługiwane są zarówno elementy docelowe wewnątrz, jak i poza nią.

 Poniższy przykład usuwa każdy plik *config* z typu elementu kompilowania.

```xml
<Target>
    <ItemGroup>
        <Compile Remove="*.config"/>
    </ItemGroup>
</Target>
```

### <a name="keepmetadata-attribute"></a><a name="BKMK_KeepMetadata"></a> KeepMetadata — atrybut

 Jeśli element jest generowany w obiekcie docelowym, element Item może zawierać `KeepMetadata` atrybut. Jeśli ten atrybut jest określony, tylko metadane określone na liście rozdzielanej średnikami nazw będą transferowane z elementu źródłowego do elementu docelowego. Pusta wartość tego atrybutu jest równoważna z nieokreśleniem go. `KeepMetadata`Atrybut został wprowadzony w .NET Framework 4,5.

 Poniższy przykład ilustruje sposób użycia `KeepMetadata` atrybutu.

```xml
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003"
ToolsVersion="4.0">

    <ItemGroup>
        <FirstItem Include="rhinoceros">
            <Class>mammal</Class>
            <Size>large</Size>
        </FirstItem>

    </ItemGroup>
    <Target Name="MyTarget">
        <ItemGroup>
            <SecondItem Include="@(FirstItem)" KeepMetadata="Class" />
        </ItemGroup>

        <Message Text="FirstItem: %(FirstItem.Identity)" />
        <Message Text="  Class: %(FirstItem.Class)" />
        <Message Text="  Size:  %(FirstItem.Size)"  />

        <Message Text="SecondItem: %(SecondItem.Identity)" />
        <Message Text="  Class: %(SecondItem.Class)" />
        <Message Text="  Size:  %(SecondItem.Size)"  />
    </Target>
</Project>

<!--
Output:
  FirstItem: rhinoceros
    Class: mammal
    Size:  large
  SecondItem: rhinoceros
    Class: mammal
    Size:
-->
```

### <a name="removemetadata-attribute"></a><a name="BKMK_RemoveMetadata"></a> RemoveMetadata — atrybut

 Jeśli element jest generowany w obiekcie docelowym, element Item może zawierać `RemoveMetadata` atrybut. Jeśli ten atrybut jest określony, wszystkie metadane są przesyłane z elementu źródłowego do elementu docelowego, z wyjątkiem metadanych, których nazwy są zawarte na liście rozdzielanych średnikami nazw. Pusta wartość tego atrybutu jest równoważna z nieokreśleniem go. `RemoveMetadata`Atrybut został wprowadzony w .NET Framework 4,5.

 Poniższy przykład ilustruje sposób użycia `RemoveMetadata` atrybutu.

```xml
<Project ToolsVersion="4.0" xmlns="http://schemas.microsoft.com/developer/msbuild/2003">

    <PropertyGroup>
        <MetadataToRemove>Size;Material</MetadataToRemove>
    </PropertyGroup>

    <ItemGroup>
        <Item1 Include="stapler">
            <Size>medium</Size>
            <Color>black</Color>
            <Material>plastic</Material>
        </Item1>
    </ItemGroup>

    <Target Name="MyTarget">
        <ItemGroup>
            <Item2 Include="@(Item1)" RemoveMetadata="$(MetadataToRemove)" />
        </ItemGroup>

        <Message Text="Item1: %(Item1.Identity)" />
        <Message Text="  Size:     %(Item1.Size)" />
        <Message Text="  Color:    %(Item1.Color)" />
        <Message Text="  Material: %(Item1.Material)" />
        <Message Text="Item2: %(Item2.Identity)" />
        <Message Text="  Size:     %(Item2.Size)" />
        <Message Text="  Color:    %(Item2.Color)" />
        <Message Text="  Material: %(Item2.Material)" />
    </Target>
</Project>

<!--
Output:
  Item1: stapler
    Size:     medium
    Color:    black
    Material: plastic
  Item2: stapler
    Size:
    Color:    black
    Material:
-->
```

### <a name="keepduplicates-attribute"></a><a name="BKMK_KeepDuplicates"></a> KeepDuplicates — atrybut

 Jeśli element jest generowany w obiekcie docelowym, element Item może zawierać `KeepDuplicates` atrybut. `KeepDuplicates` jest `Boolean` atrybutem określającym, czy element powinien zostać dodany do grupy docelowej, jeśli element jest dokładny duplikat istniejącego elementu.

 Jeśli element źródłowy i docelowy mają tę samą wartość include, ale różne metadane, element jest dodawany nawet wtedy, gdy `KeepDuplicates` jest ustawiony na `false` . Pusta wartość tego atrybutu jest równoważna z nieokreśleniem go. `KeepDuplicates`Atrybut został wprowadzony w .NET Framework 4,5.

 Poniższy przykład ilustruje sposób użycia `KeepDuplicates` atrybutu.

```xml
<Project ToolsVersion="4.0" xmlns="http://schemas.microsoft.com/developer/msbuild/2003">

    <ItemGroup>
        <Item1 Include="hourglass;boomerang" />
        <Item2 Include="hourglass;boomerang" />
    </ItemGroup>

    <Target Name="MyTarget">
        <ItemGroup>
            <Item1 Include="hourglass" KeepDuplicates="false" />
            <Item2 Include="hourglass" />
        </ItemGroup>

        <Message Text="Item1: @(Item1)" />
        <Message Text="  %(Item1.Identity)  Count: @(Item1->Count())" />
        <Message Text="Item2: @(Item2)" />
        <Message Text="  %(Item2.Identity)  Count: @(Item2->Count())" />
    </Target>
</Project>

<!--
Output:
  Item1: hourglass;boomerang
    hourglass  Count: 1
    boomerang  Count: 1
  Item2: hourglass;boomerang;hourglass
    hourglass  Count: 2
    boomerang  Count: 1
-->
```

## <a name="updating-metadata-on-items-in-an-itemgroup-outside-of-a-target"></a>Aktualizowanie metadanych dla elementów w elemencie ItemType poza elementem docelowym

Elementy poza obiektami docelowymi mogą mieć zaktualizowane metadane przy użyciu `Update` atrybutu. Ten atrybut **nie** jest dostępny dla elementów w obszarze obiekty docelowe.

```xml
<Project>
    <PropertyGroup>
        <MetadataToUpdate>pencil</MetadataToUpdate>
    </PropertyGroup>

    <ItemGroup>
        <Item1 Include="stapler">
            <Size>medium</Size>
            <Color>black</Color>
            <Material>plastic</Material>
        </Item1>
        <Item1 Include="pencil">
            <Size>small</Size>
            <Color>yellow</Color>
            <Material>wood</Material>
        </Item1>
        <Item1 Include="eraser">
            <Color>red</Color>
        </Item1>
        <Item1 Include="notebook">
            <Size>large</Size>
            <Color>white</Color>
            <Material>paper</Material>
        </Item1>

        <Item2 Include="notebook">
            <Size>SMALL</Size>
            <Color>YELLOW</Color>
        </Item2>

        <!-- Metadata can be expressed either as attributes or as elements -->
        <Item1 Update="$(MetadataToUpdate);stapler;er*r;@(Item2)" Price="10" Material="">
            <Color>RED</Color>
        </Item1>
    </ItemGroup>

    <Target Name="MyTarget">
        <Message Text="Item1: %(Item1.Identity)
    Size: %(Item1.Size)
    Color: %(Item1.Color)
    Material: %(Item1.Material)
    Price: %(Item1.Price)" />
    </Target>
</Project>

<!--  
Item1: stapler
    Size: medium
    Color: RED
    Material:
    Price: 10
Item1: pencil
    Size: small
    Color: RED
    Material:
    Price: 10
Item1: eraser
    Size:
    Color: RED
    Material:
    Price: 10
Item1: notebook
    Size: large
    Color: RED
    Material:
    Price: 10
-->
```

:::moniker range=">=vs-2019"
W programie MSBuild w wersji 16,6 lub nowszej `Update` atrybut obsługuje kwalifikowane odwołania do metadanych w celu ułatwienia importowania metadanych z dwóch lub więcej elementów.

```xml
<Project>
    <ItemGroup>
        <Item1 Include="stapler">
            <Size>medium</Size>
            <Color>black</Color>
            <Material>plastic</Material>
        </Item1>
        <Item1 Include="pencil">
            <Size>small</Size>
            <Color>yellow</Color>
            <Material>wood</Material>
        </Item1>
        <Item1 Include="eraser">
            <Size>small</Size>
            <Color>red</Color>
            <Material>gum</Material>
        </Item1>
        <Item1 Include="notebook">
            <Size>large</Size>
            <Color>white</Color>
            <Material>paper</Material>
        </Item1>

        <Item2 Include="pencil">
            <Size>MEDIUM</Size>
            <Color>RED</Color>
            <Material>PLASTIC</Material>
            <Price>10</Price>
        </Item2>

        <Item3 Include="notebook">
            <Size>SMALL</Size>
            <Color>BLUE</Color>
            <Price>20</Price>
        </Item3>

        <!-- Metadata can be expressed either as attributes or as elements -->
        <Item1 Update="@(Item2);er*r;@(Item3)" Size="%(Size)" Color="%(Item2.Color)" Price="%(Item3.Price)" Model="2020">
            <Material Condition="'%(Item2.Material)' != ''">Premium %(Item2.Material)</Material>
        </Item1>
    </ItemGroup>

    <Target Name="MyTarget">
        <Message Text="Item1: %(Item1.Identity)
    Size: %(Item1.Size)
    Color: %(Item1.Color)
    Material: %(Item1.Material)
    Price: %(Item1.Price)
    Model: %(Item1.Model)" />
    </Target>
</Project>

<!--  
Item1: stapler
    Size: medium
    Color: black
    Material: plastic
    Price:
    Model:
Item1: pencil
    Size: small
    Color: RED
    Material: Premium PLASTIC
    Price:
    Model: 2020
Item1: eraser
    Size: small
    Color:
    Material: gum
    Price:
    Model: 2020
Item1: notebook
    Size: large
    Color:
    Material: paper
    Price: 20
    Model: 2020
-->
```

Uwagi
- Niekwalifikowane metadane (% (M)) są powiązane z aktualizowanym typem elementu ( `Item1` w powyższym przykładzie). Kwalifikowane metadane ( `%(Item2.Color)` ) są powiązane z zestawem przechwyconych pasujących typów elementów z wyrażenia Update.
- Jeśli element dopasowuje się wiele razy w ramach i między wieloma elementami, do których się odwołuje:
  - Ostatnie wystąpienie każdego typu elementu, do którego występuje odwołanie, zostanie przechwycone (więc jeden przechwycony element dla każdego typu elementu).
  - Jest to zgodne z zachowaniem partii elementów zadania w obszarze obiekty docelowe.
- Gdzie jeden może umieścić odwołania%():
  - Metadane
  - Warunki metadanych
- W dopasowaniu nazw metadanych jest rozróżniana wielkość liter.
:::moniker-end

## <a name="updating-metadata-on-items-in-an-itemgroup-of-a-target"></a>Aktualizowanie metadanych dla elementów w elemencie docelowym

Metadane mogą być również modyfikowane wewnątrz elementów docelowych przez mniej wyraźną składnię niż `Update` :

```xml
<Project>
    <ItemGroup>
        <Item1 Include="stapler">
            <Size>medium</Size>
            <Color>black</Color>
            <Material>plastic</Material>
        </Item1>
        <Item1 Include="pencil">
            <Size>small</Size>
            <Color>yellow</Color>
            <Material>wood</Material>
        </Item1>
        <Item1 Include="eraser">
            <Size>small</Size>
            <Color>red</Color>
            <Material>gum</Material>
        </Item1>
        <Item1 Include="notebook">
            <Size>large</Size>
            <Color>white</Color>
            <Material>paper</Material>
        </Item1>

        <Item2 Include="pencil">
            <Size>MEDIUM</Size>
            <Color>RED</Color>
            <Material>PLASTIC</Material>
            <Price>10</Price>
        </Item2>

        <Item2 Include="ruler">
            <Color>GREEN</Color>
        </Item2>

    </ItemGroup>

    <Target Name="MyTarget">
        <ItemGroup>
            <!-- Metadata can be expressed either as attributes or as elements -->
            <Item1 Size="GIGANTIC" Color="%(Item2.Color)">
                <Material Condition="'%(Item2.Material)' != ''">Premium %(Item2.Material)</Material>
            </Item1>
        </ItemGroup>

        <Message Text="Item1: %(Item1.Identity)
    Size: %(Item1.Size)
    Color: %(Item1.Color)
    Material: %(Item1.Material)
    Price: %(Item1.Price)
    Model: %(Item1.Model)" />
    </Target>
</Project>

<!--  
Item1: stapler
    Size: GIGANTIC
    Color: GREEN
    Material: Premium PLASTIC
    Price:
    Model:
Item1: pencil
    Size: GIGANTIC
    Color: GREEN
    Material: Premium PLASTIC
    Price:
    Model:
Item1: eraser
    Size: GIGANTIC
    Color: GREEN
    Material: Premium PLASTIC
    Price:
    Model:
Item1: notebook
    Size: GIGANTIC
    Color: GREEN
    Material: Premium PLASTIC
    Price:
    Model:
-->
```

## <a name="see-also"></a>Zobacz też

- [Item — element (MSBuild)](../msbuild/item-element-msbuild.md)
- [Wspólne elementy projektów MSBuild](../msbuild/common-msbuild-project-items.md)
- [Pojęcia dotyczące programu MSBuild](../msbuild/msbuild-concepts.md)
- [MSBuild](../msbuild/msbuild.md)
- [Instrukcje: Wybieranie plików do skompilowania](../msbuild/how-to-select-the-files-to-build.md)
- [Instrukcje: wykluczanie plików z kompilacji](../msbuild/how-to-exclude-files-from-the-build.md)
- [Instrukcje: Wyświetlanie listy elementów rozdzielanych przecinkami](../msbuild/how-to-display-an-item-list-separated-with-commas.md)
- [Definicje elementów](../msbuild/item-definitions.md)
- [Przetwarzanie wsadowe](../msbuild/msbuild-batching.md)
