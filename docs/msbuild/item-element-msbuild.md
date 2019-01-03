---
title: Element — Element (MSBuild) | Dokumentacja firmy Microsoft
ms.date: 03/13/2017
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- Item Element [MSBuild]
- <Item> Element [MSBuild]
ms.assetid: dcef5f91-0613-4bfc-8ee9-d7004bb6d3a9
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: eab46fa67230ef4a42c6025d99a689ef37d213b0
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/02/2019
ms.locfileid: "53908283"
---
# <a name="item-element-msbuild"></a>Item — element (MSBuild)
Zawiera element zdefiniowany przez użytkownika i jego metadanych. Każdy element, który jest używany w [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] projekt musi być określony jako element podrzędny elementu `ItemGroup` elementu.  

 \<Project>  
 \<ItemGroup>  
 \<Element >  

## <a name="syntax"></a>Składnia  

```xml  
<Item Include="*.cs"  
        Exclude="MyFile.cs"  
        Remove="RemoveFile.cs"  
        Condition="'String A'=='String B'" >  
    <ItemMetadata1>...</ItemMetadata1>  
    <ItemMetadata2>...</ItemMetadata2>  
</Item>  
```  

## <a name="specify-metadata-as-attributes"></a>Określ metadanych jako atrybuty
W MSBuild 15.1 lub nowszym żadnych metadanych o nazwie, który jest zgodny z bieżącą listę atrybutów, opcjonalnie może być wyrażona jako atrybut.

Na przykład aby określić listę pakietów NuGet, należy zwykle użyć podobną do następującej składni.

```xml
<ItemGroup>
  <PackageReference Include="Newtonsoft.Json">
    <Version>9.0.1-beta1<Version>
  </PackageReference>
</ItemGroup>
```

Teraz, jednak można przekazać `Version` metadanych jako atrybut, taki jak następującej składni:

```xml
<ItemGroup>
  <PackageReference Include="Newtonsoft.Json" Version="9.0.1-beta1" />  
</ItemGroup>
```

## <a name="attributes-and-elements"></a>Atrybuty i elementy  
 W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.  

### <a name="attributes"></a>Atrybuty  

|Atrybut|Opis|  
|---------------|-----------------|  
|`Include`|Atrybut opcjonalny.<br /><br /> Plik lub symbol wieloznaczny, które mają zostać objęte listy elementów.|  
|`Exclude`|Atrybut opcjonalny.<br /><br /> Plik lub symbol wieloznaczny, które mają zostać wykluczone z listy elementów.|  
|`Condition`|Atrybut opcjonalny.<br /><br /> Warunek, który ma zostać obliczone. Aby uzyskać więcej informacji, zobacz [warunki](../msbuild/msbuild-conditions.md).|  
|`Remove`|Atrybut opcjonalny.<br /><br /> Plik lub symbol wieloznaczny, aby usunąć z listy elementów.<br /><br />|  
|`KeepDuplicates`|Atrybut opcjonalny.<br /><br /> Określa, czy element należy dodać do grupy docelowej, gdy jest identyczna z istniejącym elementem. Jeśli w elemencie źródłowym i docelowym mają taką samą `Include` wartość, ale innych metadanych, element jest dodano nawet wtedy, gdy `KeepDuplicates` ustawiono `false`. Aby uzyskać więcej informacji, zobacz [elementów](../msbuild/msbuild-items.md).<br /><br /> Ten atrybut jest prawidłowy tylko wtedy, gdy jest określona dla elementu w `ItemGroup` w `Target`.|  
|`KeepMetadata`|Atrybut opcjonalny.<br /><br /> Metadane dla elementów źródła do dodania do elementów docelowych. Tylko metadane, których nazwy zostały określone w liście rozdzielanej średnikami przenosi się z elementu źródłowego do elementu docelowego. Aby uzyskać więcej informacji, zobacz [elementów](../msbuild/msbuild-items.md).<br /><br /> Ten atrybut jest prawidłowy tylko wtedy, gdy jest określona dla elementu w `ItemGroup` w `Target`.|  
|`RemoveMetadata`|Atrybut opcjonalny.<br /><br /> Metadane dla elementów źródła nie są przenoszone do elementów docelowych. Wszystkie metadane są przesyłane z elementu źródłowego do docelowego elementu z wyjątkiem metadanych których nazwy są zawarte w rozdzieloną średnikami listę nazw. Aby uzyskać więcej informacji, zobacz [elementów](../msbuild/msbuild-items.md).<br /><br /> Ten atrybut jest prawidłowy tylko wtedy, gdy jest określona dla elementu w `ItemGroup` w `Target`.|  
|`Update`|Atrybut opcjonalny. (Dostępne tylko dla projektów .NET Core w programie Visual Studio 2017 lub nowszego).<br /><br /> Umożliwia modyfikowanie metadanych pliku, który został dołączony przy użyciu glob.<br /><br />  Ten atrybut jest prawidłowy tylko wtedy, gdy jest określona dla elementu w `ItemGroup` nie jest w `Target`.|  

### <a name="child-elements"></a>Elementy podrzędne  

|Element|Opis|  
|-------------|-----------------|  
|[ItemMetadata](../msbuild/itemmetadata-element-msbuild.md)|Element zdefiniowany przez użytkownika klucza metadanych, który zawiera wartość metadanych elementu. Może wynosić zero lub więcej `ItemMetadata` elementy w elemencie.|  

### <a name="parent-elements"></a>Elementy nadrzędne  

|Element|Opis|  
|-------------|-----------------|  
|[ItemGroup](../msbuild/itemgroup-element-msbuild.md)|Element grupujący elementy.|  

## <a name="remarks"></a>Uwagi  
 `Item` elementy definiowania danych wejściowych do systemu kompilacji i są grupowane w kolekcji elementów na podstawie ich nazw kolekcji zdefiniowanych przez użytkownika. Te kolekcje elementów mogą być używane jako parametry dla [zadania](../msbuild/msbuild-tasks.md), które używają poszczególnych elementów w kolekcjach wykonaj kroki procesu kompilacji. Aby uzyskać więcej informacji, zobacz [elementów](../msbuild/msbuild-items.md).  

 Przy użyciu notacji @(\<myType >) umożliwia zbieranie elementów typu \<myType > można rozszerzyć do rozdzieloną średnikami listę ciągów i przekazanego do parametru. Jeśli parametr jest typu `string`, a następnie wartość parametru znajduje się lista elementów, oddzielając je średnikami. Jeśli parametr jest tablicą ciągów (`string[]`), a następnie każdy element jest wstawiany do tablicy, na podstawie lokalizacji średnikami. Jeśli parametr zadania jest typu <xref:Microsoft.Build.Framework.ITaskItem> `[]`, wartością jest zawartość kolekcji elementów wraz z wszystkich metadanych, dołączone. Aby ograniczyć każdego elementu przy użyciu znaków innych niż średnikiem, należy użyć składni @(<myType>, "<separator>").  

 [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] Aparatu może służyć do oceny symboli wieloznacznych takich jak `*` i `?` i symboli wieloznacznych cykliczne, takie jak  */ \* \* / \*.cs*. Aby uzyskać więcej informacji, zobacz [elementów](../msbuild/msbuild-items.md).  

## <a name="examples"></a>Przykłady  
 Poniższy przykład kodu pokazuje sposób deklarowania dwóch elementów tego typu `CSFile`. Drugi zadeklarowany element zawiera metadane, który ma `MyMetadata` równa `HelloWorld`.  

```xml  
<ItemGroup>  
    <CSFile Include="engine.cs; form.cs" />  
    <CSFile Include="main.cs" >  
        <MyMetadata>HelloWorld</MyMetadata>  
    </CSFile>  
</ItemGroup>  
```  
Poniższy przykład kodu pokazuje sposób użycia `Update` atrybutu, aby zmodyfikować metadane w pliku o nazwie *somefile.cs* wchodził za pośrednictwem glob. (Dostępne tylko dla projektów .NET Core w programie Visual Studio 2017 lub nowszego).

```xml  
<ItemGroup>
    <Compile Update="somefile.cs">  // or Update="*.designer.cs"
        <MetadataKey>MetadataValue</MetadataKey>
    </Compile>
</ItemGroup>  
```  


## <a name="see-also"></a>Zobacz także  
 [Elementy](../msbuild/msbuild-items.md)   
 [Właściwości programu MSBuild](../msbuild/msbuild-properties.md)   
 [Odwołanie do schematu pliku projektu](../msbuild/msbuild-project-file-schema-reference.md)
