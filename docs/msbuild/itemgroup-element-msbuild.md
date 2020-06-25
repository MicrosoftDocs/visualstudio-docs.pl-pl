---
title: Item, element (MSBuild) | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#ItemGroup
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- ItemGroup element [MSBuild]
- <ItemGroup> element [MSBuild]
ms.assetid: aac894e3-a9f1-4bbc-a796-6ef07001f35b
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: a62b4df06d1c180a6a6d62b0231dce1136fb8059
ms.sourcegitcommit: 1d4f6cc80ea343a667d16beec03220cfe1f43b8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/23/2020
ms.locfileid: "85288978"
---
# <a name="itemgroup-element-msbuild"></a>Item, element (MSBuild)

Zawiera zestaw [elementów zdefiniowanych przez](../msbuild/item-element-msbuild.md) użytkownika. Każdy element użyty w projekcie programu MSBuild musi być określony jako element podrzędny `ItemGroup` elementu.

\<Project>
\<ItemGroup>

## <a name="syntax"></a>Składnia

```xml
<ItemGroup Condition="'String A' == 'String B'"
           Label="Label">
    <Item1>... </Item1>
    <Item2>... </Item2>
</ItemGroup>
```

## <a name="attributes-and-elements"></a>Atrybuty i elementy

W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.

### <a name="attributes"></a>Atrybuty

|Atrybut|Opis|
|---------------|-----------------|
|`Condition`|Atrybut opcjonalny. Warunek do obliczenia. Aby uzyskać więcej informacji, zobacz [warunki](../msbuild/msbuild-conditions.md).|
|`Label`|Atrybut opcjonalny. Identyfikuje `ItemGroup` . |

### <a name="child-elements"></a>Elementy podrzędne

|Element|Opis|
|-------------|-----------------|
|[Element](../msbuild/item-element-msbuild.md)|Definiuje dane wejściowe dla procesu kompilacji. Może istnieć zero lub więcej `Item` elementów w `ItemGroup` .|

### <a name="parent-elements"></a>Elementy nadrzędne

| Element | Opis |
| - | - |
| [Project](../msbuild/project-element-msbuild.md) | Wymagany element główny pliku projektu MSBuild. |
| [Obiektów](../msbuild/target-element-msbuild.md) | Począwszy od .NET Framework 3,5, `ItemGroup` element może znajdować się wewnątrz `Target` elementu. Aby uzyskać więcej informacji, zobacz [targets](../msbuild/msbuild-targets.md). |

## <a name="example"></a>Przykład

Poniższy przykład kodu pokazuje kolekcje elementów zdefiniowane przez użytkownika `Res` i `CodeFiles` zadeklarowane wewnątrz `ItemGroup` elementu. Każdy element w `Res` kolekcji elementów zawiera zdefiniowany przez użytkownika element podrzędny [ItemMetadata —](../msbuild/itemmetadata-element-msbuild.md) .

```xml
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
    <ItemGroup>
        <Res Include = "Strings.fr.resources" >
            <Culture>fr</Culture>
        </Res>
        <Res Include = "Dialogs.fr.resources" >
            <Culture>fr</Culture>
        </Res>

        <CodeFiles Include="**\*.cs" Exclude="**\generated\*.cs" />
        <CodeFiles Include="..\..\Resources\Constants.cs" />
    </ItemGroup>
...
</Project>
```

W prostym pliku projektu zwykle używany jest pojedynczy `ItemGroup` element, ale można również użyć wielu `ItemGroup` elementów. W przypadku `ItemGroup` użycia wielu elementów elementy są łączone w jeden `ItemGroup` . Na przykład niektóre elementy mogą być dołączone do oddzielnego `ItemGroup` elementu, który jest zdefiniowany w zaimportowanym pliku.

ItemGroups mogą mieć warunki stosowane przy użyciu `Condition` atrybutu. W takim przypadku elementy są dodawane do listy elementów tylko wtedy, gdy warunek jest spełniony. Zobacz [warunki MSBuild](msbuild-conditions.md)

Ten `Label` atrybut jest używany w niektórych systemach kompilacji jako sposób sterowania zachowaniami kompilacji. Można jej używać tylko w deklaracjach jako sposobu tworzenia bardziej zrozumiałych skryptów programu MSBuild lub jako ustawienia kontroli, które ma wpływ na akcje kompilacji.

## <a name="see-also"></a>Zobacz też

- [Odwołanie do schematu pliku projektu](../msbuild/msbuild-project-file-schema-reference.md)
- [Items (Elementy)](../msbuild/msbuild-items.md)
- [Wspólne elementy projektu MSBuild](../msbuild/common-msbuild-project-items.md)
