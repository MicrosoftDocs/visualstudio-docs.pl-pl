---
title: Element towaru (MSBuild) | Dokumenty firmy Microsoft
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
ms.openlocfilehash: ff7e446c319a08004260125580cdace43412cdba
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "78169355"
---
# <a name="item-element-msbuild"></a>Element elementu (MSBuild)

Zawiera element zdefiniowany przez użytkownika i jego metadane. Każdy element, który jest używany w projekcie MSBuild `ItemGroup` musi być określony jako element podrzędny elementu.

\<> \<> \<element> projektu

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

W MSBuild 15.1 lub nowszych wszelkie metadane o nazwie, która nie jest w konflikcie z bieżącą listą atrybutów, mogą być opcjonalnie wyrażone jako atrybut.

Na przykład, aby określić listę pakietów NuGet, zwykle należy użyć czegoś podobnego do następującej składni.

```xml
<ItemGroup>
  <PackageReference Include="Newtonsoft.Json">
    <Version>9.0.1-beta1<Version>
  </PackageReference>
</ItemGroup>
```

Teraz jednak można przekazać `Version` metadane jako atrybut, na przykład w następującej składni:

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
|`Include`|Atrybut opcjonalny.<br /><br /> Plik lub symbol wieloznaczny do uwzględnienia na liście elementów.|
|`Exclude`|Atrybut opcjonalny.<br /><br /> Plik lub symbol wieloznaczny do wykluczenia z listy elementów.|
|`Condition`|Atrybut opcjonalny.<br /><br /> Warunek, który ma zostać oceniony. Aby uzyskać więcej informacji, zobacz [Warunki](../msbuild/msbuild-conditions.md).|
|`Remove`|Atrybut opcjonalny.<br /><br /> Plik lub symbol wieloznaczny do usunięcia z listy elementów.<br /><br />|
|`KeepDuplicates`|Atrybut opcjonalny.<br /><br /> Określa, czy element ma zostać dodany do grupy docelowej, jeśli jest dokładnym duplikatem istniejącego elementu. Jeśli element źródłowy i `Include` docelowy mają tę samą wartość, `KeepDuplicates` ale `false`różne metadane, element jest dodawany, nawet jeśli jest ustawiony na . Aby uzyskać więcej informacji, zobacz [Elementy](../msbuild/msbuild-items.md).<br /><br /> Ten atrybut jest prawidłowy tylko wtedy, gdy `ItemGroup` jest określony dla `Target`elementu w pliku .|
|`KeepMetadata`|Atrybut opcjonalny.<br /><br /> Metadane elementów źródłowych do dodania do elementów docelowych. Tylko metadane, których nazwy są określone na liście rozdzielane średnikami są przenoszone z elementu źródłowego do elementu docelowego. Aby uzyskać więcej informacji, zobacz [Elementy](../msbuild/msbuild-items.md).<br /><br /> Ten atrybut jest prawidłowy tylko wtedy, gdy `ItemGroup` jest określony dla `Target`elementu w pliku .|
|`RemoveMetadata`|Atrybut opcjonalny.<br /><br /> Metadane dla elementów źródłowych, aby nie były przesyłane do elementów docelowych. Wszystkie metadane są przenoszone z elementu źródłowego do elementu docelowego z wyjątkiem metadanych, których nazwy znajdują się na liście nazw rozdzielonych średnikami. Aby uzyskać więcej informacji, zobacz [Elementy](../msbuild/msbuild-items.md).<br /><br /> Ten atrybut jest prawidłowy tylko wtedy, gdy `ItemGroup` jest określony dla `Target`elementu w pliku .|
|`Update`|Atrybut opcjonalny. (Dostępne tylko dla projektów .NET Core w programie Visual Studio 2017 lub nowszym).<br /><br /> Umożliwia modyfikowanie metadanych pliku, który został dołączony przy użyciu glob.<br /><br /> Ten atrybut jest prawidłowy tylko wtedy, gdy `ItemGroup` jest określony dla `Target`elementu w elemencie, który nie znajduje się w pliku .|

### <a name="child-elements"></a>Elementy podrzędne

|Element|Opis|
|-------------|-----------------|
|[ItemMetadata (Dopuszczanie elementów)](../msbuild/itemmetadata-element-msbuild.md)|Klucz metadanych elementu zdefiniowanego przez użytkownika, który zawiera wartość metadanych elementu. Może istnieć zero `ItemMetadata` lub więcej elementów w elemencie.|

### <a name="parent-elements"></a>Elementy nadrzędne

|Element|Opis|
|-------------|-----------------|
|[Itemgroup](../msbuild/itemgroup-element-msbuild.md)|Element grupowania towarów.|

## <a name="remarks"></a>Uwagi

`Item`elementy definiują dane wejściowe do systemu kompilacji i są pogrupowane w kolekcje elementów na podstawie ich nazw kolekcji zdefiniowanych przez użytkownika. Te kolekcje elementów mogą służyć jako parametry dla [zadań,](../msbuild/msbuild-tasks.md)które używają poszczególnych elementów w kolekcjach do wykonywania kroków procesu kompilacji. Aby uzyskać więcej informacji, zobacz [Elementy](../msbuild/msbuild-items.md).

Za pomocą notacji\<@( myType>) umożliwia kolekcję \<elementów typu myType> zostać rozwinięta do listy ciągów rozdzielanych średnikami i przekazana do parametru. Jeśli parametr jest `string`typu, a następnie wartość parametru jest lista elementów, oddzielone średnikami. Jeśli parametr jest tablicą ciągów (`string[]`), wówczas każdy element jest wstawiany do tablicy na podstawie lokalizacji średników. Jeśli parametr zadania jest <xref:Microsoft.Build.Framework.ITaskItem> `[]`typu, a następnie wartość jest zawartość kolekcji elementu wraz z wszelkimi metadanymi dołączone. Aby rozgraniczenie każdego elementu przy użyciu znaku innego niż średnik, należy użyć składni @(\<myType>, '\<separator>').

Aparat MSBuild może oceniać symbole wieloznaczne, takie jak `*` `?` i cykliczne symbole wieloznaczne, takie jak * / \* \* / \*cs*. Aby uzyskać więcej informacji, zobacz [Elementy](../msbuild/msbuild-items.md).

## <a name="examples"></a>Przykłady

W poniższym przykładzie kodu pokazano, `CSFile`jak zadeklarować dwa elementy typu . Drugi zadeklarowany element zawiera `MyMetadata` metadane, które mają wartość `HelloWorld`.

```xml
<ItemGroup>
    <CSFile Include="engine.cs; form.cs" />
    <CSFile Include="main.cs" >
        <MyMetadata>HelloWorld</MyMetadata>
    </CSFile>
</ItemGroup>
```

Poniższy przykład kodu pokazuje, `Update` jak użyć atrybutu do modyfikowania metadanych w pliku o nazwie *somefile.cs,* który został uwzględniony za pośrednictwem glob. (Dostępne tylko dla projektów .NET Core w programie Visual Studio 2017 lub nowszym).

```xml
<ItemGroup>
    <Compile Update="somefile.cs">  // or Update="*.designer.cs"
        <MetadataKey>MetadataValue</MetadataKey>
    </Compile>
</ItemGroup>
```

## <a name="see-also"></a>Zobacz też

- [Items](../msbuild/msbuild-items.md)
- [Typowe elementy projektu MSBuild](../msbuild/common-msbuild-project-items.md)
- [Właściwości MSBuild](../msbuild/msbuild-properties.md)
- [Odwołanie do schematu pliku projektu](../msbuild/msbuild-project-file-schema-reference.md)
