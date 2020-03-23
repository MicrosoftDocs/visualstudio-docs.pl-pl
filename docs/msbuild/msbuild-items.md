---
title: Przedmioty MSBuild | Dokumenty firmy Microsoft
description: Użyj atrybutu MSBuild Include grupy elementów, aby określić pliki, które mają zostać uwzględnione w kompilacji
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
ms.openlocfilehash: c7c41539ec50cb166dfe60690a4722992b29a47a
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "79093971"
---
# <a name="msbuild-items"></a>Elementy MSBuild

Elementy MSBuild są dane wejściowe do systemu kompilacji i zazwyczaj reprezentują `Include` pliki (pliki są określone w atrybucie). Elementy są grupowane w typy elementów na podstawie ich nazw elementów. Typy elementów są nazwane listy elementów, które mogą być używane jako parametry dla zadań. Zadania używają wartości elementu do wykonywania kroków procesu kompilacji.

 Ponieważ towary są nazwane przez typ towaru, do którego należą, terminy "element" i "wartość towaru" mogą być używane zamiennie.

## <a name="create-items-in-a-project-file"></a>Tworzenie elementów w pliku projektu

 Zadeklarować elementy w pliku projektu jako elementy podrzędne [itemGroup](../msbuild/itemgroup-element-msbuild.md) elementu. Nazwa elementu podrzędnego jest typem elementu. Atrybut `Include` elementu określa elementy (pliki), które mają być dołączone do tego typu elementu. Na przykład następujący kod XML tworzy typ `Compile`elementu o nazwie , który zawiera dwa pliki.

```xml
<ItemGroup>
    <Compile Include = "file1.cs"/>
    <Compile Include = "file2.cs"/>
</ItemGroup>
```

 *File2.cs* towaru nie zastępuje *file1.cs*towaru; Zamiast tego nazwa pliku jest dołączana do listy `Compile` wartości dla typu elementu.

 Następujący kod XML tworzy ten sam typ elementu, deklarując oba pliki w jednym `Include` atrybucie. Należy zauważyć, że nazwy plików są oddzielone średnikiem.

```xml
<ItemGroup>
    <Compile Include = "file1.cs;file2.cs"/>
</ItemGroup>
```

Atrybut `Include` jest ścieżką, która jest interpretowana względem folderu pliku projektu, $(MSBuildProjectPath), nawet jeśli element znajduje się w importowanym pliku, takim jak plik *.targets.*

## <a name="create-items-during-execution"></a>Tworzenie elementów podczas wykonywania

 Elementy, które znajdują się poza elementy [docelowe](../msbuild/target-element-msbuild.md) są przypisywane wartości podczas fazy oceny kompilacji. Podczas kolejnej fazy wykonywania elementy mogą być tworzone lub modyfikowane w następujący sposób:

- Każde zadanie może emitować element. Aby emitować element, [Task](../msbuild/task-element-msbuild.md) element musi mieć element `ItemName` [wyjściowy](../msbuild/output-element-msbuild.md) podrzędny, który ma atrybut.

- Zadanie [CreateItem](../msbuild/createitem-task.md) może emitować element. Takie użycie jest przestarzałe.

- Począwszy od programu .NET Framework `Target` 3.5, elementy mogą zawierać [ItemGroup](../msbuild/itemgroup-element-msbuild.md) elementy, które mogą zawierać elementy elementu.

## <a name="reference-items-in-a-project-file"></a>Odwoływanie się do elementów w pliku projektu

 Aby odwołać się do typów elementów w całym\<pliku projektu, należy użyć składni @( ItemType>). Na przykład należy odwołać się do typu `@(Compile)`elementu w poprzednim przykładzie za pomocą programu . Za pomocą tej składni, można przekazać elementy do zadań, określając typ elementu jako parametr tego zadania. Aby uzyskać więcej informacji, zobacz [Jak: Wybierz pliki do utworzenia](../msbuild/how-to-select-the-files-to-build.md).

 Domyślnie elementy typu towaru są oddzielone średnikami (;) po jego rozszerzeniu. Można użyć składni @(\<ItemType>,\<' separator>'), aby określić separator inny niż domyślny. Aby uzyskać więcej informacji, zobacz [Jak: Wyświetlanie listy elementów oddzielonych przecinkami](../msbuild/how-to-display-an-item-list-separated-with-commas.md).

## <a name="use-wildcards-to-specify-items"></a>Określanie elementów za pomocą symboli wieloznacznych

Za pomocą `**`znaków `*`symboli wieloznacznych i `?` symboli wieloznacznych można określić grupę plików jako dane wejściowe dla kompilacji zamiast osobno wymieniać każdy plik.

- Symbol `?` wieloznaczny pasuje do pojedynczego znaku.
- Symbol `*` wieloznaczny odpowiada zero lub więcej znaków.
- Sekwencja `**` symboli wieloznacznych pasuje do ścieżki częściowej.

Na przykład można określić `.cs` wszystkie pliki w katalogu, który zawiera plik projektu przy użyciu następującego elementu w pliku projektu.

```xml
<CSFile Include="*.cs"/>
```

Następujący element wybiera `.vb` wszystkie pliki `D:` na dysku:

```xml
<VBFile Include="D:/**/*.vb"/>
```

Jeśli chcesz dołączyć dosłowne `*` lub `?` znaki do elementu bez rozszerzeń symboli wieloznacznych, musisz uciec od [symboli wieloznacznych](../msbuild/how-to-escape-special-characters-in-msbuild.md).

Aby uzyskać więcej informacji na temat symboli wieloznacznych, zobacz [Jak: Wybieranie plików do utworzenia](../msbuild/how-to-select-the-files-to-build.md).

## <a name="use-the-exclude-attribute"></a>Użyj atrybutu Wyklucz

 Elementy elementu mogą `Exclude` zawierać atrybut, który wyklucza określone elementy (pliki) z typu elementu. Atrybut `Exclude` jest zwykle używany razem ze znakami wieloznaczymi. Na przykład następujący kod XML dodaje każdy plik *cs* w katalogu do typu elementu CSFile, z wyjątkiem pliku *DoNotBuild.cs.*

```xml
<ItemGroup>
    <CSFile  Include="*.cs"  Exclude="DoNotBuild.cs"/>
</ItemGroup>
```

 Atrybut `Exclude` ma wpływ tylko na elementy, `Include` które są dodawane przez atrybut w elemencie elementu, który zawiera je zarówno. Poniższy przykład nie wyklucza *pliku Form1.cs*, który został dodany w poprzednim elemencie elementu.

```xml
<Compile Include="*.cs" />
<Compile Include="*.res" Exclude="Form1.cs">
```

 Aby uzyskać więcej informacji, zobacz [Jak: Wykluczanie plików z kompilacji](../msbuild/how-to-exclude-files-from-the-build.md).

## <a name="item-metadata"></a>Metadane elementu

 Elementy mogą zawierać metadane oprócz `Include` informacji `Exclude` w i atrybuty. Te metadane mogą być używane przez zadania, które wymagają więcej informacji o elementach lub do zadań wsadowych i obiektów docelowych. Aby uzyskać więcej informacji, zobacz [Batching](../msbuild/msbuild-batching.md).

 Metadane to zbiór par klucz-wartość, które są zadeklarowane w pliku projektu jako elementy podrzędne elementu elementu. Nazwa elementu podrzędnego jest nazwą metadanych, a wartość elementu podrzędnego jest wartością metadanych.

 Metadane są skojarzone z elementem, który go zawiera. Na przykład następujący kod `Culture` XML dodaje metadane, które mają wartość `Fr` zarówno do *one.cs,* jak i *two.cs* elementów typu elementu CSFile.

```xml
<ItemGroup>
    <CSFile Include="one.cs;two.cs">
        <Culture>Fr</Culture>
    </CSFile>
</ItemGroup>
```

 Element może mieć zero lub więcej wartości metadanych. Wartości metadanych można zmienić w dowolnym momencie. Jeśli ustawisz metadane na pustą wartość, skutecznie usunąć je z kompilacji.

### <a name="reference-item-metadata-in-a-project-file"></a><a name="BKMK_ReferencingItemMetadata"></a>Metadane elementu odwołania w pliku projektu

 Metadane elementu można odwoływać się do metadanych\<elementu w całym pliku projektu przy użyciu składni %( ItemMetadataName>). Jeśli istnieje niejednoznaczność, można zakwalifikować odwołanie przy użyciu nazwy typu elementu. Na przykład można określić\<%( ItemType.ItemMetaDataName>). W poniższym przykładzie użyto wyświetlają metadane do partii Message zadanie. Aby uzyskać więcej informacji na temat używania metadanych elementu do przetwarzania wsadowego, zobacz [Metadane elementu w wsadowaniu wsadowym zadań](../msbuild/item-metadata-in-task-batching.md).

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

### <a name="well-known-item-metadata"></a><a name="BKMK_WellKnownItemMetadata"></a>Dobrze znane metadane elementu

 Gdy element jest dodawany do typu elementu, ten element jest przypisany niektóre dobrze znane metadane. Na przykład wszystkie elementy mają dobrze znane\<metadane %( Nazwa pliku>), którego wartość jest nazwą pliku elementu (bez rozszerzenia). Aby uzyskać więcej informacji, zobacz [Znane metadane elementu](../msbuild/msbuild-well-known-item-metadata.md).

### <a name="transform-item-types-by-using-metadata"></a><a name="BKMK_Transforming"></a>Przekształcanie typów elementów przy użyciu metadanych

 Listy elementów można przekształcić w nowe listy elementów przy użyciu metadanych. Na przykład można przekształcić typ `CppFiles` elementu, który zawiera elementy reprezentujące pliki *cpp,* w odpowiednią `@(CppFiles -> '%(Filename).obj')`listę plików *obj* przy użyciu wyrażenia .

 Poniższy kod `CultureResource` tworzy typ elementu, który `EmbeddedResource` zawiera `Culture` kopie wszystkich elementów z metadanymi. Wartość `Culture` metadanych staje się wartością `CultureResource.TargetDirectory`nowych metadanych .

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

 Aby uzyskać więcej informacji, zobacz [Przekształcenia](../msbuild/msbuild-transforms.md).

## <a name="item-definitions"></a>Definicje elementów

 Począwszy od programu .NET Framework 3.5, można dodać domyślne metadane do dowolnego typu elementu przy użyciu [elementu ItemDefinitionGroup](../msbuild/itemdefinitiongroup-element-msbuild.md). Podobnie jak dobrze znane metadane, domyślne metadane są skojarzone ze wszystkimi elementami o określonym typie elementu. Domyślne metadane można jawnie zastąpić w definicji elementu. Na przykład następujący kod XML daje `Compile` elementy *one.cs* i *three.cs* metadanych `BuildDay` z wartością "Poniedziałek". Kod daje element *two.cs* metadanych `BuildDay` o wartości "Wtorek".

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

 Aby uzyskać więcej informacji, zobacz [Definicje elementów](../msbuild/item-definitions.md).

## <a name="attributes-for-items-in-an-itemgroup-of-a-target"></a>Atrybuty elementów w grupie przedmiotów obiektu docelowego

 Począwszy od programu .NET Framework `Target` 3.5, elementy mogą zawierać [ItemGroup](../msbuild/itemgroup-element-msbuild.md) elementy, które mogą zawierać elementy elementu. Atrybuty w tej sekcji są prawidłowe, gdy `ItemGroup` są określone `Target`dla elementu w .

### <a name="remove-attribute"></a><a name="BKMK_RemoveAttribute"></a>Usuń atrybut

 Atrybut `Remove` usuwa określone elementy (pliki) z typu elementu. Ten atrybut został wprowadzony w .NET Framework 3.5 (tylko wewnątrz obiektów docelowych). Zarówno wewnątrz, jak i na zewnątrz obiekty docelowe są obsługiwane począwszy od MSBuild 15.0.

 Poniższy przykład usuwa każdy plik *.config* z typu elementu kompilacji.

```xml
<Target>
    <ItemGroup>
        <Compile Remove="*.config"/>
    </ItemGroup>
</Target>
```

### <a name="keepmetadata-attribute"></a><a name="BKMK_KeepMetadata"></a>Atrybut KeepMetadata

 Jeśli element jest generowany w obrębie obiektu docelowego, element elementu może zawierać `KeepMetadata` atrybut. Jeśli ten atrybut jest określony, tylko metadane, które są określone na liście nazw rozdzielane średnikami zostaną przeniesione z elementu źródłowego do elementu docelowego. Pusta wartość dla tego atrybutu jest odpowiednikiem nieokreślenia go. Atrybut `KeepMetadata` został wprowadzony w .NET Framework 4.5.

 Poniższy przykład ilustruje `KeepMetadata` sposób użycia atrybutu.

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

### <a name="removemetadata-attribute"></a><a name="BKMK_RemoveMetadata"></a>Atrybut Usuń metadane

 Jeśli element jest generowany w obrębie obiektu docelowego, element elementu może zawierać `RemoveMetadata` atrybut. Jeśli ten atrybut jest określony, wszystkie metadane są przenoszone z elementu źródłowego do elementu docelowego z wyjątkiem metadanych, których nazwy znajdują się na liście nazw rozdzielonych średnikami. Pusta wartość dla tego atrybutu jest odpowiednikiem nieokreślenia go. Atrybut `RemoveMetadata` został wprowadzony w .NET Framework 4.5.

 Poniższy przykład ilustruje `RemoveMetadata` sposób użycia atrybutu.

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

### <a name="keepduplicates-attribute"></a><a name="BKMK_KeepDuplicates"></a>Atrybut KeepDuplicates

 Jeśli element jest generowany w obrębie obiektu docelowego, element elementu może zawierać `KeepDuplicates` atrybut. `KeepDuplicates`jest `Boolean` atrybutem, który określa, czy element powinien zostać dodany do grupy docelowej, jeśli element jest dokładnym duplikatem istniejącego elementu.

 Jeśli element źródłowy i docelowy mają taką samą wartość Include, ale różne metadane, element jest dodawany, nawet jeśli `KeepDuplicates` jest ustawiony na `false`. Pusta wartość dla tego atrybutu jest odpowiednikiem nieokreślenia go. Atrybut `KeepDuplicates` został wprowadzony w .NET Framework 4.5.

 Poniższy przykład ilustruje `KeepDuplicates` sposób użycia atrybutu.

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

## <a name="see-also"></a>Zobacz też

- [Element elementu (MSBuild)](../msbuild/item-element-msbuild.md)
- [Typowe elementy projektu MSBuild](../msbuild/common-msbuild-project-items.md)
- [Koncepcje MSBuild](../msbuild/msbuild-concepts.md)
- [Msbuild](../msbuild/msbuild.md)
- [Jak: Wybierz pliki do utworzenia](../msbuild/how-to-select-the-files-to-build.md)
- [Jak: Wykluczanie plików z kompilacji](../msbuild/how-to-exclude-files-from-the-build.md)
- [Jak: Wyświetlanie listy elementów oddzielonych przecinkami](../msbuild/how-to-display-an-item-list-separated-with-commas.md)
- [Definicje elementów](../msbuild/item-definitions.md)
- [Tworzenie partii](../msbuild/msbuild-batching.md)
