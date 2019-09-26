---
title: Elementy MSBuild | Microsoft Docs
description: Użyj atrybutu dołączania MSBuild elementu Item, aby określić pliki do uwzględnienia w kompilacji
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- MSBuild, Items
ms.assetid: d762eff4-c92a-4b5f-a944-1ca30aa22319
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: cebf824785fed39cfd824b9b90f9d19be5df8c64
ms.sourcegitcommit: e98db44f3a33529b0ba188d24390efd09e548191
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/25/2019
ms.locfileid: "71251713"
---
# <a name="msbuild-items"></a>Elementy programu MSBuild
Elementy programu MSBuild są wejściami do systemu kompilacji i zazwyczaj reprezentują pliki (pliki są określone w `Include` atrybucie). Elementy są pogrupowane w typy elementów na podstawie ich nazw elementów. Typy elementów są nazwanymi elementami, które mogą być używane jako parametry zadań. Zadania używają wartości elementów do wykonania kroków procesu kompilacji.

 Ponieważ elementy są nazwane przez typ elementu, do którego należą, można użyć zamiennie warunków "Item" i "value Item".

## <a name="create-items-in-a-project-file"></a>Tworzenie elementów w pliku projektu
 Elementy w pliku projektu deklaruje się jako elementy podrzędne elementu [Item](../msbuild/itemgroup-element-msbuild.md) . Nazwa elementu podrzędnego jest typem elementu. `Include` Atrybut elementu określa elementy (pliki), które mają być dołączone do tego typu elementu. Na przykład poniższy kod XML tworzy typ elementu o nazwie `Compile`, który zawiera dwa pliki.

```xml
<ItemGroup>
    <Compile Include = "file1.cs"/>
    <Compile Include = "file2.cs"/>
</ItemGroup>
```

 Element *file2.cs* nie zastępuje elementu *file1.cs*; Zamiast tego nazwa pliku jest dołączana do listy wartości `Compile` typu elementu.

 Poniższy kod XML tworzy ten sam typ elementu przez zadeklarowanie obu plików w `Include` jednym atrybucie. Należy zauważyć, że nazwy plików są oddzielone średnikami.

```xml
<ItemGroup>
    <Compile Include = "file1.cs;file2.cs"/>
</ItemGroup>
```

## <a name="create-items-during-execution"></a>Tworzenie elementów podczas wykonywania
 Elementy, które są poza elementami [docelowymi](../msbuild/target-element-msbuild.md) , są przypisane do wartości w fazie oceny kompilacji. Podczas kolejnej fazy wykonywania elementy mogą być tworzone lub modyfikowane w następujący sposób:

- Każde zadanie może emitować element. Aby emitować element, element [Task](../msbuild/task-element-msbuild.md) musi mieć podrzędny element [wyjściowy](../msbuild/output-element-msbuild.md) `ItemName` , który ma atrybut.

- Zadanie [elementu "Item](../msbuild/createitem-task.md) " może emitować element. Takie użycie jest przestarzałe.

- Począwszy od .NET Framework 3,5, `Target` elementy mogą zawierać elementy elementu [Item](../msbuild/itemgroup-element-msbuild.md) , które mogą zawierać elementy Item.

## <a name="reference-items-in-a-project-file"></a>Elementy referencyjne w pliku projektu
 Aby odwołać się do typów elementów w całym pliku projektu, należy użyć składni\<@ (ItemType >). Na przykład, można odwołać się do typu elementu w poprzednim przykładzie przy użyciu `@(Compile)`. Za pomocą tej składni można przekazać elementy do zadań, określając typ elementu jako parametr tego zadania. Aby uzyskać więcej informacji, zobacz [jak: Wybierz pliki do skompilowania](../msbuild/how-to-select-the-files-to-build.md).

 Domyślnie elementy typu elementu są oddzielone średnikami (;) po jego rozszerzeniu. Aby określić separator inny niż domyślny,\<można użyć składni @\<(ItemType >, "separator >"). Aby uzyskać więcej informacji, zobacz [jak: Wyświetla listę elementów rozdzieloną przecinkami](../msbuild/how-to-display-an-item-list-separated-with-commas.md).

## <a name="use-wildcards-to-specify-items"></a>Użyj symboli wieloznacznych, aby określić elementy

Możesz użyć `**` `?` symboli wieloznacznych, `*`aby określić grupę plików jako dane wejściowe dla kompilacji, a nie osobno wymieniać każdy plik.

- `?` Symbol wieloznaczny dopasowuje pojedynczy znak.
- `*` Symbol wieloznaczny dopasowuje zero lub więcej znaków.
- Sekwencja `**` znaków wieloznacznych jest zgodna ze ścieżką częściową.

Na przykład można określić wszystkie `.cs` pliki w katalogu, który zawiera plik projektu, przy użyciu następującego elementu w pliku projektu.

```xml
<CSFile Include="*.cs"/>
```

Następujący element wybiera wszystkie `.vb` pliki `D:` na dysku:

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

 Ten `Exclude` atrybut ma wpływ tylko na elementy, które są dodawane `Include` przez atrybut w elemencie elementu, który zawiera te wartości. W poniższym przykładzie nie można wykluczyć pliku *Form1.cs*, który został dodany w poprzednim elemencie elementu.

```xml
<Compile Include="*.cs" />
<Compile Include="*.res" Exclude="Form1.cs">
```

 Aby uzyskać więcej informacji, zobacz [jak: Wyklucz pliki z kompilacji](../msbuild/how-to-exclude-files-from-the-build.md).

## <a name="item-metadata"></a>Metadane elementu
 Elementy mogą zawierać metadane oprócz informacji w `Include` atrybutach i. `Exclude` Te metadane mogą służyć do zadań, które wymagają więcej informacji na temat elementów lub zadań wsadowych i elementów docelowych. Aby uzyskać więcej informacji, zobacz Tworzenie [pakietów wsadowych](../msbuild/msbuild-batching.md).

 Metadata jest kolekcją par klucz-wartość, które są zadeklarowane w pliku projektu jako elementy podrzędne elementu elementu. Nazwa elementu podrzędnego jest nazwą metadanych, a wartością elementu podrzędnego jest wartość metadanych.

 Metadane są skojarzone z elementem elementu, który go zawiera. Na przykład poniższy `Culture` kod XML dodaje metadane, które mają wartość `Fr` zarówno *one.cs* , jak i *Two.cs* elementów typu CSFile.

```xml
<ItemGroup>
    <CSFile Include="one.cs;two.cs">
        <Culture>Fr</Culture>
    </CSFile>
</ItemGroup>
```

 Element może mieć zero lub więcej wartości metadanych. Wartości metadanych można zmienić w dowolnym momencie. Jeśli ustawisz metadane na wartość pustą, możesz skutecznie usunąć ją z kompilacji.

### <a name="BKMK_ReferencingItemMetadata"></a>Metadane elementu odwołania w pliku projektu
 Metadane elementu można odwoływać w całym pliku projektu przy użyciu składni%(\<ItemMetaDataName >). Jeśli istnieje niejednoznaczność, można kwalifikować odwołanie przy użyciu nazwy typu elementu. Na przykład można określić%(\<ItemType. ItemMetaDataName >). Poniższy przykład używa metadanych wyświetlania do wsadowego zadania wiadomości. Aby uzyskać więcej informacji o sposobach używania metadanych elementu na potrzeby tworzenia pakietów wsadowych, zobacz [metadane elementu w usłudze Batch zadania](../msbuild/item-metadata-in-task-batching.md).

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

### <a name="BKMK_WellKnownItemMetadata"></a>Metadane dobrze znanego elementu
 Gdy element zostanie dodany do typu elementu, do tego elementu są przypisane pewne dobrze znane metadane. Na przykład wszystkie elementy mają dobrze znaną%(\<nazwę pliku metadanych >), której wartość jest nazwą pliku elementu. Aby uzyskać więcej informacji, zobacz [dobrze znane metadane elementu](../msbuild/msbuild-well-known-item-metadata.md).

### <a name="BKMK_Transforming"></a>Przekształcanie typów elementów za pomocą metadanych
 Listy elementów można przekształcać na nowe listy elementów przy użyciu metadanych. Na przykład można `CppFiles` przekształcić typ elementu zawierający elementy, które reprezentują pliki *. cpp* , do odpowiedniej listy plików *. obj* przy użyciu wyrażenia. `@(CppFiles -> '%(Filename).obj')`

 Poniższy kod tworzy `CultureResource` typ elementu zawierający kopie wszystkich `EmbeddedResource` elementów z `Culture` metadanymi. Wartość metadanych jest wartością nowego metadanych `CultureResource.TargetDirectory`. `Culture`

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
 Począwszy od .NET Framework 3,5, można dodać domyślne metadane do dowolnego typu elementu przy użyciu [elementu ItemDefinitionGroup](../msbuild/itemdefinitiongroup-element-msbuild.md). Podobnie jak dobrze znane metadane, domyślne metadane są skojarzone ze wszystkimi elementami typu elementu określonego przez użytkownika. Można jawnie przesłonić domyślne metadane w definicji elementu. Na przykład poniższy `Compile` kod XML daje elementy *one.cs* i *Three.cs* metadane `BuildDay` z wartością "poniedziałek". Kod nadaje elementowi *Two.cs* metadane `BuildDay` z wartością "wtorek".

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
 Począwszy od .NET Framework 3,5, `Target` elementy mogą zawierać elementy elementu [Item](../msbuild/itemgroup-element-msbuild.md) , które mogą zawierać elementy Item. Atrybuty w tej sekcji są prawidłowe, jeśli są określone dla elementu w `ItemGroup` `Target`elemencie.

### <a name="BKMK_RemoveAttribute"></a>Usuń atrybut
 Ten `Remove` atrybut usuwa określone elementy (pliki) z typu elementu. Ten atrybut został wprowadzony w .NET Framework 3,5 (tylko wewnątrz elementów docelowych). W programie MSBuild 15,0 obsługiwane są zarówno elementy docelowe wewnątrz, jak i poza nią.

 Poniższy przykład usuwa każdy plik *config* z typu elementu kompilowania.

```xml
<Target>
    <ItemGroup>
        <Compile Remove="*.config"/>
    </ItemGroup>
</Target>
```

### <a name="BKMK_KeepMetadata"></a>KeepMetadata — atrybut
 Jeśli element jest generowany w obiekcie docelowym, element Item może zawierać `KeepMetadata` atrybut. Jeśli ten atrybut jest określony, tylko metadane określone na liście rozdzielanej średnikami nazw będą transferowane z elementu źródłowego do elementu docelowego. Pusta wartość tego atrybutu jest równoważna z nieokreśleniem go. `KeepMetadata` Atrybut został wprowadzony w .NET Framework 4,5.

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

### <a name="BKMK_RemoveMetadata"></a>RemoveMetadata — atrybut
 Jeśli element jest generowany w obiekcie docelowym, element Item może zawierać `RemoveMetadata` atrybut. Jeśli ten atrybut jest określony, wszystkie metadane są przesyłane z elementu źródłowego do elementu docelowego, z wyjątkiem metadanych, których nazwy są zawarte na liście rozdzielanych średnikami nazw. Pusta wartość tego atrybutu jest równoważna z nieokreśleniem go. `RemoveMetadata` Atrybut został wprowadzony w .NET Framework 4,5.

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

### <a name="BKMK_KeepDuplicates"></a>KeepDuplicates — atrybut
 Jeśli element jest generowany w obiekcie docelowym, element Item może zawierać `KeepDuplicates` atrybut. `KeepDuplicates``Boolean` jest atrybutem określającym, czy element powinien zostać dodany do grupy docelowej, jeśli element jest dokładny duplikat istniejącego elementu.

 Jeśli element źródłowy i docelowy mają tę samą wartość include, ale różne metadane, element jest dodawany nawet wtedy, `KeepDuplicates` gdy jest ustawiony `false`na. Pusta wartość tego atrybutu jest równoważna z nieokreśleniem go. `KeepDuplicates` Atrybut został wprowadzony w .NET Framework 4,5.

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

## <a name="see-also"></a>Zobacz także
- [Item — element (MSBuild)](../msbuild/item-element-msbuild.md)
- [Wspólne elementy projektu MSBuild](../msbuild/common-msbuild-project-items.md)
- [Pojęcia dotyczące programu MSBuild](../msbuild/msbuild-concepts.md)
- [MSBuild](../msbuild/msbuild.md)
- [Instrukcje: Wybierz pliki do skompilowania](../msbuild/how-to-select-the-files-to-build.md)
- [Instrukcje: Wyklucz pliki z kompilacji](../msbuild/how-to-exclude-files-from-the-build.md)
- [Instrukcje: Wyświetl listę elementów rozdzieloną przecinkami](../msbuild/how-to-display-an-item-list-separated-with-commas.md)
- [Definicje elementów](../msbuild/item-definitions.md)
- [Przetwarzanie wsadowe](../msbuild/msbuild-batching.md)
