---
title: Item — element (MSBuild) | Microsoft Docs
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
ms.openlocfilehash: 730e7d317ffa3fd5a450978f35659df3fe5629f3
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/01/2020
ms.locfileid: "75573667"
---
# <a name="item-element-msbuild"></a>Item — element (MSBuild)
Zawiera element zdefiniowany przez użytkownika i jego metadane. Każdy element, który jest używany w projekcie [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] musi być określony jako element podrzędny elementu `ItemGroup`.

\<Project > \<Itemmanager > \<

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

Teraz można jednak przekazać metadane `Version` jako atrybut, na przykład w następującej składni:

```xml
<ItemGroup>
  <PackageReference Include="Newtonsoft.Json" Version="9.0.1-beta1" />
</ItemGroup>
```

## <a name="attributes-and-elements"></a>Atrybuty i elementy
 W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.

### <a name="attributes"></a>{1&gt;{2&gt;Atrybuty&lt;2}&lt;1}

|Atrybut|Opis|
|---------------|-----------------|
|`Include`|Atrybut opcjonalny.<br /><br /> Plik lub symbol wieloznaczny do dołączenia do listy elementów.|
|`Exclude`|Atrybut opcjonalny.<br /><br /> Plik lub symbol wieloznaczny do wykluczenia z listy elementów.|
|`Condition`|Atrybut opcjonalny.<br /><br /> Warunek, który ma zostać obliczony. Aby uzyskać więcej informacji, zobacz [warunki](../msbuild/msbuild-conditions.md).|
|`Remove`|Atrybut opcjonalny.<br /><br /> Plik lub symbol wieloznaczny do usunięcia z listy elementów.<br /><br />|
|`KeepDuplicates`|Atrybut opcjonalny.<br /><br /> Określa, czy element powinien zostać dodany do grupy docelowej, jeśli jest to dokładny duplikat istniejącego elementu. Jeśli element źródłowy i docelowy mają tę samą `Include` wartość, ale różne metadane, element jest dodawany nawet wtedy, gdy `KeepDuplicates` jest ustawiona na `false`. Aby uzyskać więcej informacji, zobacz [Items](../msbuild/msbuild-items.md).<br /><br /> Ten atrybut jest prawidłowy tylko wtedy, gdy jest określony dla elementu w `ItemGroup`, który znajduje się w `Target`.|
|`KeepMetadata`|Atrybut opcjonalny.<br /><br /> Metadane elementów źródłowych do dodania do elementów docelowych. Tylko metadane, których nazwy są określone na liście rozdzielanej średnikami, są przesyłane z elementu źródłowego do elementu docelowego. Aby uzyskać więcej informacji, zobacz [Items](../msbuild/msbuild-items.md).<br /><br /> Ten atrybut jest prawidłowy tylko wtedy, gdy jest określony dla elementu w `ItemGroup`, który znajduje się w `Target`.|
|`RemoveMetadata`|Atrybut opcjonalny.<br /><br /> Metadane elementów źródłowych, które nie są przekazywane do elementów docelowych. Wszystkie metadane są przesyłane z elementu źródłowego do elementu docelowego, z wyjątkiem metadanych, których nazwy są zawarte na liście rozdzielanych średnikami nazw. Aby uzyskać więcej informacji, zobacz [Items](../msbuild/msbuild-items.md).<br /><br /> Ten atrybut jest prawidłowy tylko wtedy, gdy jest określony dla elementu w `ItemGroup`, który znajduje się w `Target`.|
|`Update`|Atrybut opcjonalny. (Dostępne tylko dla projektów .NET Core w programie Visual Studio 2017 lub nowszym).<br /><br /> Umożliwia modyfikowanie metadanych pliku, który został uwzględniony przy użyciu globalizowania.<br /><br /> Ten atrybut jest prawidłowy tylko wtedy, gdy jest określony dla elementu w `ItemGroup`, który nie znajduje się w `Target`.|

### <a name="child-elements"></a>Elementy podrzędne

|Element|Opis|
|-------------|-----------------|
|[ItemMetadata](../msbuild/itemmetadata-element-msbuild.md)|Klucz metadanych elementu zdefiniowany przez użytkownika, który zawiera wartość metadanych elementu. Element może mieć co najmniej zero elementów `ItemMetadata`.|

### <a name="parent-elements"></a>Elementy nadrzędne

|Element|Opis|
|-------------|-----------------|
|[ItemGroup](../msbuild/itemgroup-element-msbuild.md)|Element grupujący dla elementów.|

## <a name="remarks"></a>Uwagi
elementy `Item` definiują dane wejściowe w systemie kompilacji i są pogrupowane w kolekcje elementów na podstawie ich nazw kolekcji zdefiniowanych przez użytkownika. Te kolekcje elementów mogą służyć jako parametry [zadań](../msbuild/msbuild-tasks.md), które używają poszczególnych elementów w kolekcjach do wykonywania kroków procesu kompilacji. Aby uzyskać więcej informacji, zobacz [Items](../msbuild/msbuild-items.md).

Użycie notacji @ (\<myType >) umożliwia zbieranie elementów typu \<myType > do rozdzielenia średnikami list ciągów i przekazanie do parametru. Jeśli parametr jest typu `string`, wartość parametru jest listą elementów rozdzielonych średnikami. Jeśli parametr jest tablicą ciągów (`string[]`), każdy element zostanie wstawiony do tablicy na podstawie lokalizacji średników. Jeśli parametr zadania jest typu <xref:Microsoft.Build.Framework.ITaskItem>`[]`, wartość jest zawartością kolekcji elementów wraz z dowolnymi dołączonymi metadanymi. Aby rozdzielić każdy element przy użyciu znaku innego niż średnik, użyj składni @ (\<myType >,\<separator > ").

Aparat [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] może oszacować symbole wieloznaczne, takie jak `*` i `?` oraz cykliczne symbole wieloznaczne, takie jak */\*\*/\*. cs*. Aby uzyskać więcej informacji, zobacz [Items](../msbuild/msbuild-items.md).

## <a name="examples"></a>Przykłady
Poniższy przykład kodu pokazuje, jak zadeklarować dwa elementy typu `CSFile`. Drugi zadeklarowany element zawiera metadane, który ma `MyMetadata` ustawiony na `HelloWorld`.

```xml
<ItemGroup>
    <CSFile Include="engine.cs; form.cs" />
    <CSFile Include="main.cs" >
        <MyMetadata>HelloWorld</MyMetadata>
    </CSFile>
</ItemGroup>
```

Poniższy przykład kodu pokazuje, jak używać atrybutu `Update` do modyfikowania metadanych w pliku o nazwie *SOMEFILE.cs* , który został dołączony za pośrednictwem globalizowania. (Dostępne tylko dla projektów .NET Core w programie Visual Studio 2017 lub nowszym).

```xml
<ItemGroup>
    <Compile Update="somefile.cs">  // or Update="*.designer.cs"
        <MetadataKey>MetadataValue</MetadataKey>
    </Compile>
</ItemGroup>
```

## <a name="see-also"></a>Zobacz także
- [Elementy](../msbuild/msbuild-items.md)
- [Wspólne elementy projektu MSBuild](../msbuild/common-msbuild-project-items.md)
- [Właściwości programu MSBuild](../msbuild/msbuild-properties.md)
- [Odwołanie do schematu pliku projektu](../msbuild/msbuild-project-file-schema-reference.md)
