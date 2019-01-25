---
title: Element — Element (MSBuild) | Dokumentacja firmy Microsoft
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
ms.openlocfilehash: b45d0e9494700d03c0e96ccd0708e2754b4f7a2b
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54797028"
---
# <a name="item-element-msbuild"></a>Item — Element (MSBuild)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
Zawiera element zdefiniowany przez użytkownika i jego metadanych. Każdy element, który jest używany w [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] projekt musi być określony jako element podrzędny elementu `ItemGroup` elementu.  
  
 \<Project>  
 \<ItemGroup>  
 \<Element >  
  
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
|`Include`|Atrybut wymagany.<br /><br /> Plik lub symbol wieloznaczny, które mają zostać objęte listy elementów.|  
|`Exclude`|Atrybut opcjonalny.<br /><br /> Plik lub symbol wieloznaczny, które mają zostać wykluczone z listy elementów.|  
|`Condition`|Atrybut opcjonalny.<br /><br /> Warunek, który ma zostać obliczone. Aby uzyskać więcej informacji, zobacz [warunki](../msbuild/msbuild-conditions.md).|  
|`Remove`|Atrybut opcjonalny.<br /><br /> Plik lub symbol wieloznaczny, aby usunąć z listy elementów.<br /><br /> Ten atrybut jest prawidłowy tylko wtedy, gdy jest określona dla elementu w `ItemGroup` w `Target`.|  
|`KeepMetadata`|Atrybut opcjonalny.<br /><br /> Metadane dla elementów źródła do dodania do elementów docelowych. Tylko metadane, których nazwy zostały określone w liście rozdzielanej średnikami przenosi się z elementu źródłowego do elementu docelowego. Aby uzyskać więcej informacji, zobacz [elementów](../msbuild/msbuild-items.md).<br /><br /> Ten atrybut jest prawidłowy tylko wtedy, gdy jest określona dla elementu w `ItemGroup` w `Target`.|  
|`RemoveMetadata`|Atrybut opcjonalny.<br /><br /> Metadane dla elementów źródła nie są przenoszone do elementów docelowych. Wszystkie metadane są przesyłane z elementu źródłowego do docelowego elementu z wyjątkiem metadanych których nazwy są zawarte w rozdzieloną średnikami listę nazw. Aby uzyskać więcej informacji, zobacz [elementów](../msbuild/msbuild-items.md).<br /><br /> Ten atrybut jest prawidłowy tylko wtedy, gdy jest określona dla elementu w `ItemGroup` w `Target`.|  
|`KeepDuplicates`|Atrybut opcjonalny.<br /><br /> Określa, czy element należy dodać do grupy docelowej, gdy jest identyczna z istniejącym elementem. Jeśli w elemencie źródłowym i docelowym mają taką samą `Include` wartość, ale innych metadanych, element jest dodano nawet wtedy, gdy `KeepDuplicates` ustawiono `false`. Aby uzyskać więcej informacji, zobacz [elementów](../msbuild/msbuild-items.md).<br /><br /> Ten atrybut jest prawidłowy tylko wtedy, gdy jest określona dla elementu w `ItemGroup` w `Target`.|  
  
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
  
 Przy użyciu notacji `@(` *myType* `)` Włącza kolekcję elementów typu *myType* można rozszerzyć do rozdzieloną średnikami listę ciągów i przekazanego do parametru. Jeśli parametr jest typu `string`, a następnie wartość parametru znajduje się lista elementów, oddzielając je średnikami. Jeśli parametr jest tablicą ciągów (`string[]`), a następnie każdy element jest wstawiany do tablicy, na podstawie lokalizacji średnikami. Jeśli parametr zadania jest typu <xref:Microsoft.Build.Framework.ITaskItem> `[]`, wartością jest zawartość kolekcji elementów wraz z wszystkich metadanych, dołączone. Aby ograniczyć każdego elementu przy użyciu znaków innych niż średnikiem, należy użyć składni `@(` *myType*`, '`*separator*`')`.  
  
 [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] Aparatu może służyć do oceny symboli wieloznacznych takich jak `*` i `?` i symboli wieloznacznych cykliczne, takie jak `/**/*.cs`. Aby uzyskać więcej informacji, zobacz [elementów](../msbuild/msbuild-items.md).  
  
## <a name="example"></a>Przykład  
 Poniższy przykład kodu pokazuje sposób deklarowania dwóch elementów tego typu `CSFile`. Drugi zadeklarowany element zawiera metadane, który ma `MyMetadata` równa `HelloWorld`.  
  
```  
<ItemGroup>  
    <CSFile Include="engine.cs; form.cs" />  
    <CSFile Include="main.cs" >  
        <MyMetadata>HelloWorld</MyMetadata>  
    </CSFile>  
</ItemGroup>  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Elementy](../msbuild/msbuild-items.md)   
 [Właściwości programu MSBuild](msbuild-properties1.md)   
 [Odwołanie do schematu pliku projektu](../msbuild/msbuild-project-file-schema-reference.md)
