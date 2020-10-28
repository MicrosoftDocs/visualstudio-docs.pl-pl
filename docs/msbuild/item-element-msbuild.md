---
title: Item — element (MSBuild) | Microsoft Docs
description: Dowiedz się, w jaki sposób MSBuild używa elementu Item do wyświetlania elementu zdefiniowanego przez użytkownika i jego metadanych. Każdy element musi być elementem podrzędnym elementu elementu.
ms.custom: SEO-VS-2020
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
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 51ecf68cacf0edca90893931642cd7fb6064f972
ms.sourcegitcommit: f1d47655974a2f08e69704a9a0c46cb007e51589
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/28/2020
ms.locfileid: "92904646"
---
# <a name="item-element-msbuild"></a>Item — element (MSBuild)

Zawiera element zdefiniowany przez użytkownika i jego metadane. Każdy element, który jest używany w projekcie MSBuild, musi być określony jako element podrzędny `ItemGroup` elementu.

\<Project>
\<ItemGroup>
\<Item>

## <a name="syntax"></a>Składnia

```xml
<Item Include="*.cs"
        Exclude="MyFile.cs"
        Condition="'String A'=='String B'">
    <ItemMetadata1>...</ItemMetadata1>
    <ItemMetadata2>...</ItemMetadata2>
</Item>
```

## <a name="specify-metadata-as-attributes"></a>Określanie metadanych jako atrybutów

W programie MSBuild 15,1 lub nowszym wszelkie metadane o nazwie, która nie powoduje konfliktu z bieżącą listą atrybutów, mogą być opcjonalnie wyrażone jako atrybut.

Na przykład, aby określić listę pakietów NuGet, zazwyczaj należy użyć podobnej do następującej składni.

```xml
<ItemGroup>
  <PackageReference Include="Newtonsoft.Json">
    <Version>9.0.1-beta1<Version>
  </PackageReference>
</ItemGroup>
```

Teraz można jednak przekazać `Version` metadane jako atrybut, na przykład w następującej składni:

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
|`Include`|Atrybut opcjonalny.<br /><br /> Plik lub symbol wieloznaczny do dołączenia do listy elementów.|
|`Exclude`|Atrybut opcjonalny.<br /><br /> Plik lub symbol wieloznaczny do wykluczenia z listy elementów.|
|`Condition`|Atrybut opcjonalny.<br /><br /> Warunek, który ma zostać obliczony. Aby uzyskać więcej informacji, zobacz [warunki](../msbuild/msbuild-conditions.md).|
|`Remove`|Atrybut opcjonalny.<br /><br /> Plik lub symbol wieloznaczny do usunięcia z listy elementów.<br /><br />|
|`KeepDuplicates`|Atrybut opcjonalny.<br /><br /> Określa, czy element powinien zostać dodany do grupy docelowej, jeśli jest to dokładny duplikat istniejącego elementu. Jeśli element źródłowy i docelowy mają tę samą `Include` wartość, ale różne metadane, element jest dodawany nawet wtedy, gdy `KeepDuplicates` jest ustawiony na `false` . Aby uzyskać więcej informacji, zobacz [Items](../msbuild/msbuild-items.md).<br /><br /> Ten atrybut jest prawidłowy tylko wtedy, gdy jest określony dla elementu w elemencie `ItemGroup` `Target` .|
|`KeepMetadata`|Atrybut opcjonalny.<br /><br /> Metadane elementów źródłowych do dodania do elementów docelowych. Tylko metadane, których nazwy są określone na liście rozdzielanej średnikami, są przesyłane z elementu źródłowego do elementu docelowego. Aby uzyskać więcej informacji, zobacz [Items](../msbuild/msbuild-items.md).<br /><br /> Ten atrybut jest prawidłowy tylko wtedy, gdy jest określony dla elementu w elemencie `ItemGroup` `Target` .|
|`RemoveMetadata`|Atrybut opcjonalny.<br /><br /> Metadane elementów źródłowych, które nie są przekazywane do elementów docelowych. Wszystkie metadane są przesyłane z elementu źródłowego do elementu docelowego, z wyjątkiem metadanych, których nazwy są zawarte na liście rozdzielanych średnikami nazw. Aby uzyskać więcej informacji, zobacz [Items](../msbuild/msbuild-items.md).<br /><br /> Ten atrybut jest prawidłowy tylko wtedy, gdy jest określony dla elementu w elemencie `ItemGroup` `Target` .|
|`Update`|Atrybut opcjonalny. (Dostępne tylko dla projektów .NET Core w programie Visual Studio 2017 lub nowszym).<br /><br /> Umożliwia modyfikowanie metadanych elementu. zwykle używany do przesłonięcia domyślnych metadanych określonych elementów po określeniu grupy elementów intially (na przykład z symbolem wieloznacznym).<br /><br /> Ten atrybut jest prawidłowy tylko wtedy, gdy jest określony dla elementu w elemencie `ItemGroup` , który nie znajduje się w `Target` .|

### <a name="child-elements"></a>Elementy podrzędne

|Element|Opis|
|-------------|-----------------|
|[ItemMetadata —](../msbuild/itemmetadata-element-msbuild.md)|Klucz metadanych elementu zdefiniowany przez użytkownika, który zawiera wartość metadanych elementu. Element może mieć zero lub więcej `ItemMetadata` elementów.|

### <a name="parent-elements"></a>Elementy nadrzędne

|Element|Opis|
|-------------|-----------------|
|[ItemGroup](../msbuild/itemgroup-element-msbuild.md)|Element grupujący dla elementów.|

## <a name="remarks"></a>Uwagi

`Item` elementy definiują dane wejściowe w systemie kompilacji i są pogrupowane w kolekcje elementów na podstawie ich nazw kolekcji zdefiniowanych przez użytkownika. Te kolekcje elementów mogą służyć jako parametry [zadań](../msbuild/msbuild-tasks.md), które używają poszczególnych elementów w kolekcjach do wykonywania kroków procesu kompilacji. Aby uzyskać więcej informacji, zobacz [Items](../msbuild/msbuild-items.md).

Użycie notacji @ ( \<myType> ) umożliwia rozwinięcie kolekcji elementów typu do \<myType> listy ciągów rozdzielanych średnikami i przekazanie do parametru. Jeśli parametr jest typu `string` , wartość parametru jest listą elementów rozdzielonych średnikami. Jeśli parametr jest tablicą ciągów ( `string[]` ), każdy element zostanie wstawiony do tablicy na podstawie lokalizacji średników. Jeśli parametr zadania jest typu <xref:Microsoft.Build.Framework.ITaskItem> `[]` , wartość jest zawartość kolekcji elementów wraz z dowolnymi dołączonymi metadanymi. Aby rozdzielić każdy element przy użyciu znaku innego niż średnik, użyj składni @ ( \<myType> , " \<separator> ").

Aparat MSBuild może oceniać symbole wieloznaczne, takie jak `*` i `?` i cykliczne symbole wieloznaczne, takie jak */ \* \* / \* . cs* . Aby uzyskać więcej informacji, zobacz [Items](../msbuild/msbuild-items.md).

## <a name="examples"></a>Przykłady

Poniższy przykład kodu pokazuje, jak zadeklarować dwa elementy typu `CSFile` . Drugi zadeklarowany element zawiera metadane, który ma `MyMetadata` ustawioną wartość `HelloWorld` .

```xml
<ItemGroup>
    <CSFile Include="engine.cs; form.cs" />
    <CSFile Include="main.cs" >
        <MyMetadata>HelloWorld</MyMetadata>
    </CSFile>
</ItemGroup>
```

Poniższy przykład kodu pokazuje, jak używać `Update` atrybutu do modyfikowania metadanych w pliku o nazwie *SOMEFILE.cs* , który został dołączony za pośrednictwem globalizowania. (Dostępne tylko dla projektów .NET Core w programie Visual Studio 2017 lub nowszym).

```xml
<ItemGroup>
    <Compile Update="somefile.cs">  // or Update="*.designer.cs"
        <MetadataKey>MetadataValue</MetadataKey>
    </Compile>
</ItemGroup>
```

## <a name="see-also"></a>Zobacz także

- [Elementy](../msbuild/msbuild-items.md)
- [Wspólne elementy projektów MSBuild](../msbuild/common-msbuild-project-items.md)
- [właściwości programu MSBuild](../msbuild/msbuild-properties.md)
- [Odwołanie do schematu pliku projektu](../msbuild/msbuild-project-file-schema-reference.md)
