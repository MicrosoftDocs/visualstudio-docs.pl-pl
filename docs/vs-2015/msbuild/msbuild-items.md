---
title: Elementy programu MSBuild | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
ms.topic: reference
helpviewer_keywords:
- MSBuild, Items
ms.assetid: d762eff4-c92a-4b5f-a944-1ca30aa22319
caps.latest.revision: 38
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: deeed2ed86b07ec6f3d36f7dd4b4be02c1060155
ms.sourcegitcommit: 53aa5a413717a1b62ca56a5983b6a50f7f0663b3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/17/2019
ms.locfileid: "59669812"
---
# <a name="msbuild-items"></a>Elementy programu MSBuild
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Elementy programu MSBuild to wejścia do systemu kompilacji i zazwyczaj reprezentują pliki. Elementy są grupowane w typy elementów na podstawie ich nazw elementu. Typy elementów są nazywane listy elementów, które mogą być używane jako parametry dla zadań. Zadania umożliwiają wartości elementu wykonaj kroki procesu kompilacji.  
  
 Ponieważ elementy są reprezentowane przez typ elementu, do których one należą, warunki "item" i "wartość elementu" może służyć zamiennie.  
  
 **W tym temacie**  
  
-   [Tworzenie pozycji przechowywanych w pliku projektu](#BKMK_Creating1)  
  
-   [Tworzenie elementów podczas wykonywania](#BKMK_Creating2)  
  
-   [Odwoływanie się do elementów w pliku projektu](#BKMK_ReferencingItems)  
  
-   [Przy użyciu symboli wieloznacznych do określenia elementów](#BKMK_Wildcards)  
  
-   [Za pomocą atrybutu wykluczania](#BKMK_ExcludeAttribute)  
  
-   [Metadane elementu](#BKMK_ItemMetadata)  
  
    -   [Odwoływanie się do metadanych elementu w pliku projektu](#BKMK_ReferencingItemMetadata)  
  
    -   [Metadane dobrze znanego elementu](#BKMK_WellKnownItemMetadata)  
  
    -   [Przekształcanie typów elementów przy użyciu metadanych](#BKMK_Transforming)  
  
-   [Definicje elementów](#BKMK_ItemDefinitions)  
  
-   [Atrybuty elementów w ItemGroup obiektu docelowego](#BKMK_AttributesWithinTargets)  
  
    -   [Usuń atrybut](#BKMK_RemoveAttribute)  
  
    -   [KeepMetadata Attribute](#BKMK_KeepMetadata)  
  
    -   [RemoveMetadata Attribute](#BKMK_RemoveMetadata)  
  
    -   [Atrybut KeepDuplicates](#BKMK_KeepDuplicates)  
  
##  <a name="BKMK_Creating1"></a> Tworzenie pozycji przechowywanych w pliku projektu  
 Możesz deklarować elementów w pliku projektu jako element podrzędny elementy [ItemGroup](../msbuild/itemgroup-element-msbuild.md) elementu. Nazwa elementu podrzędnego jest typ elementu. `Include` Atrybut elementu określa elementy (pliki) do uwzględnienia z tego typu elementu. Na przykład, następujący kod XML tworzy typ elementu, który nosi nazwę `Compile`, który zawiera dwa pliki.  
  
```  
<ItemGroup>  
    <Compile Include = "file1.cs"/>  
    <Compile Include = "file2.cs"/>  
</ItemGroup>  
```  
  
 Element "file2.cs" nie zastępuje element "file1.cs"; Zamiast tego, nazwa pliku jest dołączany do listy wartości dla `Compile` typ elementu. Nie można usunąć elementu z typu elementu, w fazie obliczania kompilacji.  
  
 Następujący kod XML tworzy tego samego typu elementu przez zadeklarowanie oba pliki w jednym `Include` atrybutu. Należy zauważyć, że nazwy plików są oddzielone średnikami.  
  
```  
<ItemGroup>  
    <Compile Include = "file1.cs;file2.cs"/>  
</ItemGroup>  
```  
  
##  <a name="BKMK_Creating2"></a> Tworzenie elementów podczas wykonywania  
 Elementy, które wykraczają poza [docelowej](../msbuild/target-element-msbuild.md) elementy mają przypisane wartości w fazie obliczania kompilacji. W fazie wykonanie kolejnych elementów można utworzyć lub zmodyfikować w następujący sposób:  
  
-   Każde zadanie może emitować elementu. Aby emitować elementu [zadań](../msbuild/task-element-msbuild.md) element musi mieć element podrzędny [dane wyjściowe](../msbuild/output-element-msbuild.md) element, który ma `ItemName` atrybutu.  
  
-   [Createitem —](../msbuild/createitem-task.md) zadanie może emitować elementu. Takie użycie jest przestarzałe.  
  
-   Począwszy od programu .NET Framework 3.5 `Target` elementy mogą zawierać [ItemGroup](../msbuild/itemgroup-element-msbuild.md) elementy, które mogą zawierać elementu elementów.  
  
##  <a name="BKMK_ReferencingItems"></a> Odwoływanie się do elementów w pliku projektu  
 Aby odwoływać się do typów elementów w całym pliku projektu, należy użyć składni @(`ItemType`). Na przykład czy odwołanie do typu elementu w poprzednim przykładzie za pomocą `@(Compile)`. Przy użyciu tej składni, elementy można przekazać do zadania, określając typ elementu jako parametr danego zadania. Aby uzyskać więcej informacji, zobacz [jak: Wybieranie plików do kompilacji](../msbuild/how-to-select-the-files-to-build.md).  
  
 Domyślnie elementów typu elementu są oddzielone średnikami (;), gdy jest on rozwinięty. Można używać składni @(*ItemType*, "*separator*") do określenia separator inną niż domyślna. Aby uzyskać więcej informacji, zobacz [jak: Wyświetlanie listy elementów rozdzielanych przecinkami](../msbuild/how-to-display-an-item-list-separated-with-commas.md).  
  
##  <a name="BKMK_Wildcards"></a> Przy użyciu symboli wieloznacznych do określenia elementów  
 Możesz użyć **, \*, a? znaki symboli wieloznacznych, aby określić grupy plików jako dane wejściowe dla kompilacji, zamiast wymieniać każdy plik oddzielnie.  
  
- ? wieloznaczny pasuje do pojedynczego znaku.  
  
- * Wieloznacznego dopasowuje zero lub więcej znaków.  
  
- ** Ścieżka częściowa pasuje do sekwencji znaków symboli wieloznacznych.  
  
  Na przykład można określić wszystkie pliki .cs w katalogu, który zawiera plik projektu za pomocą następującego elementu w pliku projektu.  
  
```  
<CSFile Include="*.cs"/>  
```  
  
 Następujący element wybiera wszystkie pliki .vb na dysku D::  
  
```  
<VBFile Include="D:/**/*.vb"/>  
```  
  
 Aby uzyskać więcej informacji na temat symboli wieloznacznych, zobacz [jak: Wybieranie plików do kompilacji](../msbuild/how-to-select-the-files-to-build.md).  
  
##  <a name="BKMK_ExcludeAttribute"></a> Za pomocą atrybutu wykluczania  
 Może zawierać elementów `Exclude` atrybut, który wyklucza określone elementy (pliki) z tego typu elementu. `Exclude` Atrybut jest zwykle używana wraz z symboli wieloznacznych. Na przykład następujący kod XML dodaje każdego pliku .cs, w tym katalogu do typu elementu CSFile, z wyjątkiem `DoNotBuild.cs` pliku.  
  
```  
<ItemGroup>  
    <CSFile  Include="*.cs"  Exclude="DoNotBuild.cs"/>  
</ItemGroup>  
```  
  
 `Exclude` Atrybut ma wpływ na elementy, które są dodawane przez `Include` atrybutu w elemencie elementu, który zawiera oba te. Poniższy przykład w takich sytuacjach przydałaby Wyklucz plik Form1.cs, który został dodany w poprzedniej pozycji elementu.  
  
```  
<Compile Include="*.cs" />  
<Compile Include="*.res" Exclude="Form1.cs">  
```  
  
 Aby uzyskać więcej informacji, zobacz [jak: Wykluczanie plików z kompilacji](../msbuild/how-to-exclude-files-from-the-build.md).  
  
##  <a name="BKMK_ItemMetadata"></a> Metadane elementu  
 Elementy może zawierać metadane, oprócz tych informacji w `Include` i `Exclude` atrybutów. Te metadane może służyć przez zadania podrzędne, które wymagają więcej informacji o elementach lub cele i zadania podrzędne usługi batch. Aby uzyskać więcej informacji, zobacz [przetwarzania wsadowego](../msbuild/msbuild-batching.md).  
  
 Metadane są kolekcję par klucz wartość, które są zadeklarowane w pliku projektu jako elementy podrzędne elementu. Nazwa elementu podrzędnego jest nazwa metadanych, a wartość elementu podrzędnego jest wartość metadanych.  
  
 Metadane są skojarzone z elementem elementu, który go zawiera. Na przykład następujący kod XML dodaje `Culture` metadanych, który ma wartość `Fr` zarówno "one.cs" i "two.cs" elementy CSFile typ elementu.  
  
```  
<ItemGroup>  
    <CSFile Include="one.cs;two.cs">  
        <Culture>Fr</Culture>  
    </CSFile>  
</ItemGroup>  
```  
  
 Element może mieć zero lub więcej wartości metadanych. W dowolnym momencie można zmienić wartości metadanych. Jeśli metadanych jest ustawiona na wartość pustą, efektywnie usuniesz go z kompilacji.  
  
###  <a name="BKMK_ReferencingItemMetadata"></a> Odwoływanie się do metadanych elementu w pliku projektu  
 Metadane elementu w całym pliku projektu można odwoływać się przy użyciu składni %(`ItemMetadataName`). Jeśli istnieje niejednoznaczność, masz prawo odwołanie za pomocą nazwy typu elementu. Adapterem, możesz określić %(*ItemType.ItemMetaDataName*). W poniższym przykładzie użyto Wyświetla metadane partii zadań wiadomości. Aby uzyskać więcej informacji o sposobie używania metadane elementu dla przetwarzania wsadowego, zobacz [metadane elementu w przetwarzaniu wsadowym zadań](../msbuild/item-metadata-in-task-batching.md).  
  
```  
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
  
###  <a name="BKMK_WellKnownItemMetadata"></a> Metadane dobrze znanego elementu  
 Gdy element zostanie dodany do typu elementu, ten element jest przypisywany niektóre metadane dobrze znanego. Na przykład, wszystkie elementy mają dobrze znanych metadanych `%(Filename)`, którego wartością jest nazwa pliku elementu. Aby uzyskać więcej informacji, zobacz [metadane dobrze znanego elementu](../msbuild/msbuild-well-known-item-metadata.md).  
  
###  <a name="BKMK_Transforming"></a> Przekształcanie typów elementów przy użyciu metadanych  
 Przy użyciu metadanych, można przekształcić elementu listy do nowego elementu listy. Na przykład można przekształcać typ elementu `CppFiles` zawierający elementy, które reprezentują pliki .cpp do odpowiedniej listy plików .obj przy użyciu wyrażenia `@(CppFiles -> '%(Filename).obj')`.  
  
 Poniższy kod tworzy `CultureResource` typ, który zawiera kopię wszystkich elementu `EmbeddedResource` elementy z `Culture` metadanych. `Culture` Wartości metadanych staje się wartością z nowymi metadanymi `CultureResource.TargetDirectory`.  
  
```  
<Target Name="ProcessCultureResources">  
    <ItemGroup>  
        <CultureResource Include="@(EmbeddedResource)"  
            Condition="'%(EmbeddedResource.Culture)' != ''">  
            <TargetDirectory>%(EmbeddedResource.Culture) </TargetDirectory>  
        </CultureResource>  
    </ItemGroup>  
</Target>  
```  
  
 Aby uzyskać więcej informacji, zobacz [przekształca](../msbuild/msbuild-transforms.md).  
  
##  <a name="BKMK_ItemDefinitions"></a> Definicje elementów  
 Począwszy od programu .NET Framework 3.5, można dodać domyślnego metadanych do dowolnego typu elementu za pomocą [ItemDefinitionGroup — element](../msbuild/itemdefinitiongroup-element-msbuild.md). Metadane dobrze znanego, np. metadanych domyślne jest skojarzony z wszystkich elementów tego typu elementu, który określisz. Można jawnie przesłonić domyślny metadanych w definicji elementu. Na przykład następujący kod XML daje `Compile` elementów "one.cs" i "three.cs" metadanych `BuildDay` z wartością "Poniedziałek". Ten kod zawiera element "two.cs" metadanych `BuildDay` z wartością "Wtorek".  
  
```  
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
  
##  <a name="BKMK_AttributesWithinTargets"></a> Atrybuty elementów w ItemGroup obiektu docelowego  
 Począwszy od programu .NET Framework 3.5 `Target` elementy mogą zawierać [ItemGroup](../msbuild/itemgroup-element-msbuild.md) elementy, które mogą zawierać elementu elementów. Atrybuty w tej sekcji są prawidłowe w przypadku, gdy są one określone dla elementu w `ItemGroup` w `Target`.  
  
###  <a name="BKMK_RemoveAttribute"></a> Usuń atrybut  
 Elementy w `ItemGroup` obiektu docelowego może zawierać `Remove` atrybut, który usuwa określone elementy (pliki) z tego typu elementu. Ten atrybut został wprowadzony w programie .NET Framework 3.5.  
  
 Poniższy przykład usuwa każdy plik .config z typu elementu kompilacji.  
  
```  
<Target>  
    <ItemGroup>  
        <Compile Remove="*.config"/>  
    </ItemGroup>  
</Target>  
```  
  
###  <a name="BKMK_KeepMetadata"></a> KeepMetadata Attribute  
 Jeśli element jest generowany w elemencie docelowym, może zawierać elementu `KeepMetadata` atrybutu. Jeśli ten atrybut jest określony, metadane, który jest określony w rozdzieloną średnikami listę nazw zostaną przesłane z elementu źródłowego do elementu docelowego. Pusta wartość dla tego atrybutu jest odpowiednikiem nie określając jej. `KeepMetadata` Atrybut wprowadzono w programie .NET Framework 4.5.  
  
 Poniższy przykład ilustruje sposób używania `KeepMetadata` atrybutu.  
  
```  
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
  
###  <a name="BKMK_RemoveMetadata"></a> Atrybut RemoveMetadata  
 Jeśli element jest generowany w elemencie docelowym, może zawierać elementu `RemoveMetadata` atrybutu. Jeśli ten atrybut jest określony, wszystkie metadane są przesyłane z elementu źródłowego do elementu docelowego, z wyjątkiem metadanych których nazwy są zawarte w rozdzieloną średnikami listę nazw. Pusta wartość dla tego atrybutu jest odpowiednikiem nie określając jej. `RemoveMetadata` Atrybut wprowadzono w programie .NET Framework 4.5.  
  
 Poniższy przykład ilustruje sposób używania `RemoveMetadata` atrybutu.  
  
```  
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
  
###  <a name="BKMK_KeepDuplicates"></a> KeepDuplicates Attribute  
 Jeśli element jest generowany w elemencie docelowym, może zawierać elementu `KeepDuplicates` atrybutu. `KeepDuplicates` jest `Boolean` atrybut, który określa, czy element należy dodać do grupy docelowej, jeśli element jest identyczna z istniejącym elementem.  
  
 Jeśli w elemencie źródłowym i docelowym mają taką samą wartość Include, ale innych metadanych, element jest dodawany nawet wtedy, gdy `KeepDuplicates` ustawiono `false`. Pusta wartość dla tego atrybutu jest odpowiednikiem nie określając jej. `KeepDuplicates` Atrybut wprowadzono w programie .NET Framework 4.5.  
  
 Poniższy przykład ilustruje sposób używania `KeepDuplicates` atrybutu.  
  
```  
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
 [Pojęcia dotyczące programu MSBuild](../msbuild/msbuild-concepts.md)  
 [Program MSBuild](msbuild.md)   
 [Instrukcje: Wybieranie plików do kompilacji](../msbuild/how-to-select-the-files-to-build.md)   
 [Instrukcje: Wykluczanie plików z kompilacji](../msbuild/how-to-exclude-files-from-the-build.md)   
 [Instrukcje: Wyświetlanie listy elementów rozdzielanych przecinkami](../msbuild/how-to-display-an-item-list-separated-with-commas.md)   
 [Definicje elementów](../msbuild/item-definitions.md)   
 [Przetwarzanie wsadowe](../msbuild/msbuild-batching.md)   
 [Item, element (MSBuild)](../msbuild/item-element-msbuild.md)
