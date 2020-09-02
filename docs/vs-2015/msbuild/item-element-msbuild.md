---
title: Item — element (MSBuild) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- Item Element [MSBuild]
- <Item> Element [MSBuild]
ms.assetid: dcef5f91-0613-4bfc-8ee9-d7004bb6d3a9
caps.latest.revision: 34
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: cc3d606bb890b5f95089bfc7b1e83b2d34cd56ba
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "68192607"
---
# <a name="item-element-msbuild"></a>Item — Element (MSBuild)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Zawiera element zdefiniowany przez użytkownika i jego metadane. Każdy element, który jest używany w [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] projekcie, musi być określony jako element podrzędny `ItemGroup` elementu.  
  
 \<Project>  
 \<ItemGroup>  
 \<Item>  
  
## <a name="syntax"></a>Składnia  
  
```  
<Item Include="*.cs"  
        Exclude="MyFile.cs"  
        Remove="RemoveFile.cs"  
        Condition="'String A'=='String B'" >  
    <ItemMetadata1>...</ItemMetadata1>  
    <ItemMetadata2>...</ItemMetadata2>  
</Item>  
```  
  
## <a name="attributes-and-elements"></a>Atrybuty i elementy  
 W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.  
  
### <a name="attributes"></a>Atrybuty  
  
|Atrybut|Opis|  
|---------------|-----------------|  
|`Include`|Atrybut wymagany.<br /><br /> Plik lub symbol wieloznaczny do dołączenia do listy elementów.|  
|`Exclude`|Atrybut opcjonalny.<br /><br /> Plik lub symbol wieloznaczny do wykluczenia z listy elementów.|  
|`Condition`|Atrybut opcjonalny.<br /><br /> Warunek, który ma zostać obliczony. Aby uzyskać więcej informacji, zobacz [warunki](../msbuild/msbuild-conditions.md).|  
|`Remove`|Atrybut opcjonalny.<br /><br /> Plik lub symbol wieloznaczny do usunięcia z listy elementów.<br /><br /> Ten atrybut jest prawidłowy tylko wtedy, gdy jest określony dla elementu w elemencie `ItemGroup` `Target` .|  
|`KeepMetadata`|Atrybut opcjonalny.<br /><br /> Metadane elementów źródłowych do dodania do elementów docelowych. Tylko metadane, których nazwy są określone na liście rozdzielanej średnikami, są przesyłane z elementu źródłowego do elementu docelowego. Aby uzyskać więcej informacji, zobacz [Items](../msbuild/msbuild-items.md).<br /><br /> Ten atrybut jest prawidłowy tylko wtedy, gdy jest określony dla elementu w elemencie `ItemGroup` `Target` .|  
|`RemoveMetadata`|Atrybut opcjonalny.<br /><br /> Metadane elementów źródłowych, które nie są przekazywane do elementów docelowych. Wszystkie metadane są przesyłane z elementu źródłowego do elementu docelowego, z wyjątkiem metadanych, których nazwy są zawarte na liście rozdzielanych średnikami nazw. Aby uzyskać więcej informacji, zobacz [Items](../msbuild/msbuild-items.md).<br /><br /> Ten atrybut jest prawidłowy tylko wtedy, gdy jest określony dla elementu w elemencie `ItemGroup` `Target` .|  
|`KeepDuplicates`|Atrybut opcjonalny.<br /><br /> Określa, czy element powinien zostać dodany do grupy docelowej, jeśli jest to dokładny duplikat istniejącego elementu. Jeśli element źródłowy i docelowy mają tę samą `Include` wartość, ale różne metadane, element jest dodawany nawet wtedy, gdy `KeepDuplicates` jest ustawiony na `false` . Aby uzyskać więcej informacji, zobacz [Items](../msbuild/msbuild-items.md).<br /><br /> Ten atrybut jest prawidłowy tylko wtedy, gdy jest określony dla elementu w elemencie `ItemGroup` `Target` .|  
  
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
  
 Użycie notacji `@(` *MyType* `)` umożliwia rozszerzanie kolekcji elementów typu *MyType* na listę ciągów rozdzielanych średnikami i przekazanie do parametru. Jeśli parametr jest typu `string` , wartość parametru jest listą elementów rozdzielonych średnikami. Jeśli parametr jest tablicą ciągów ( `string[]` ), każdy element zostanie wstawiony do tablicy na podstawie lokalizacji średników. Jeśli parametr zadania jest typu <xref:Microsoft.Build.Framework.ITaskItem> `[]` , wartość jest zawartość kolekcji elementów wraz z dowolnymi dołączonymi metadanymi. Aby rozgraniczać każdy element przy użyciu znaku innego niż średnik, użyj `@(` *myType* `, '` *separatora*MyType składni `')` .  
  
 [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)]Aparat może oszacować symbole wieloznaczne, takie jak `*` i `?` i cykliczne symbole wieloznaczne, takie jak `/**/*.cs` . Aby uzyskać więcej informacji, zobacz [Items](../msbuild/msbuild-items.md).  
  
## <a name="example"></a>Przykład  
 Poniższy przykład kodu pokazuje, jak zadeklarować dwa elementy typu `CSFile` . Drugi zadeklarowany element zawiera metadane, który ma `MyMetadata` ustawioną wartość `HelloWorld` .  
  
```  
<ItemGroup>  
    <CSFile Include="engine.cs; form.cs" />  
    <CSFile Include="main.cs" >  
        <MyMetadata>HelloWorld</MyMetadata>  
    </CSFile>  
</ItemGroup>  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Produktów](../msbuild/msbuild-items.md)   
 [Właściwości programu MSBuild](msbuild-properties1.md)   
 [Odwołanie do schematu pliku projektu](../msbuild/msbuild-project-file-schema-reference.md)
