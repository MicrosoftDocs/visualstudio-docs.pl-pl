---
title: Przekształcenia programu MSBuild | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- MSBuild, transforms
- transforms [MSBuild]
ms.assetid: d0bcfc3c-14fa-455e-805c-63ccffa4a3bf
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 34394ba35a349a1564f6c3fdd43052be3e1fdf03
ms.sourcegitcommit: 96737c54162f5fd5c97adef9b2d86ccc660b2135
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/26/2020
ms.locfileid: "77633112"
---
# <a name="msbuild-transforms"></a>Przekształcenia programu MSBuild

Transformacja jest konwersją jeden do jednego z jednej listy elementów na inną. Poza umożliwieniem projektowi konwersji list elementów, transformacja umożliwia obiektowi docelowemu znalezienie bezpośredniego mapowania między danymi wejściowymi i wyjściowymi. W tym temacie objaśniono transformacje i sposób, w jaki MSBuild używa ich do bardziej wydajnego kompilowania projektów.

## <a name="transform-modifiers"></a>Przekształć Modyfikatory

Przekształcenia nie są dowolne, ale są ograniczone przez specjalną składnię, w której wszystkie Modyfikatory transformacji muszą mieć format%(\<ItemMetaDataName >). Wszystkie metadane elementu mogą być używane jako modyfikator przekształcania. Obejmuje to metadane dobrze znanego elementu, które są przypisywane do każdego elementu podczas jego tworzenia. Aby uzyskać listę dobrze znanych metadanych elementu, zobacz [dobrze znane metadane elementu](../msbuild/msbuild-well-known-item-metadata.md).

W poniższym przykładzie lista plików *resx* jest przekształcana na listę plików *resources* . Modyfikator przekształcenia% (filename) określa, że każdy plik *resources* ma taką samą nazwę jak plik. *resx* .

```xml
@(RESXFile->'%(filename).resources')
```

Na przykład jeśli elementy na liście elementów @ (RESXFile) to *Form1. resx*, *Form2. resx*i *Form3. resx*, dane wyjściowe na liście przekształconej będą takie jak *Form1. resources*, *Form2. resources*i *Form3. resources*.

> [!NOTE]
> Możesz określić niestandardowy separator dla listy przekształconych elementów w ten sam sposób, w jaki określisz separator dla standardowej listy elementów. Na przykład aby oddzielić listę przekształconych elementów przy użyciu przecinka (,) zamiast domyślnego średnika (;), użyj następującego kodu XML: `@(RESXFile->'Toolset\%(filename)%(extension)', ',')`

## <a name="use-multiple-modifiers"></a>Używanie wielu modyfikatorów

 Wyrażenie przekształcenia może zawierać wiele modyfikatorów, które mogą być połączone w dowolnej kolejności i mogą być powtarzane. W poniższym przykładzie nazwa katalogu zawierającego pliki jest zmieniana, ale pliki zachowują oryginalną nazwę i rozszerzenie nazwy pliku.

```xml
@(RESXFile->'Toolset\%(filename)%(extension)')
```

 Na przykład, jeśli elementy znajdujące się na liście elementów `RESXFile` są *Project1\Form1.resx*, *Project1\Form2.resx*i *Project1\Form3.Text*, dane wyjściowe na liście przekształconej będą *Toolset\Form1.resx*, *Toolset\Form2.resx*i *Toolset\Form3.Text*.

## <a name="dependency-analysis"></a>Analiza zależności

 Transformacje gwarantują mapowanie jeden do jednego między listą przekształconych elementów a listą pierwotnych elementów. W związku z tym, jeśli obiekt docelowy tworzy dane wyjściowe, które są przekształcane, program MSBuild może analizować sygnatury czasowe wejść i wyjść, a także zdecydować, czy pominąć, skompilować lub częściowo skompilować element docelowy.

 W poniższym przykładzie [zadania Copy](../msbuild/copy-task.md) każdy plik na liście elementów `BuiltAssemblies` mapuje do pliku w folderze docelowym zadania, określonym przy użyciu transformacji w atrybucie `Outputs`. Jeśli plik na liście elementów `BuiltAssemblies` ulegnie zmianie, zadanie `Copy` zostanie uruchomione tylko dla zmienionego pliku, a wszystkie inne pliki zostaną pominięte. Aby uzyskać więcej informacji na temat analizy zależności i sposobu używania transformacji, zobacz [How to: build przyrostowo](../msbuild/how-to-build-incrementally.md).

```xml
<Target Name="CopyOutputs"
    Inputs="@(BuiltAssemblies)"
    Outputs="@(BuiltAssemblies -> '$(OutputPath)%(Filename)%(Extension)')">

    <Copy
        SourceFiles="@(BuiltAssemblies)"
        DestinationFolder="$(OutputPath)"/>

</Target>
```

## <a name="example"></a>Przykład

### <a name="description"></a>Opis

 Poniższy przykład pokazuje plik projektu MSBuild, który używa transformacji. W tym przykładzie przyjęto założenie, że w katalogu *c:\sub0\sub1\sub2\sub3* istnieje tylko jeden plik *XSD* , a katalog roboczy to *c:\sub0*.

### <a name="code"></a>Kod

```xml
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
    <ItemGroup>
        <Schema Include="sub1\**\*.xsd"/>
    </ItemGroup>

    <Target Name="Messages">
        <Message Text="rootdir: @(Schema->'%(rootdir)')"/>
        <Message Text="fullpath: @(Schema->'%(fullpath)')"/>
        <Message Text="rootdir + directory + filename + extension: @(Schema->'%(rootdir)%(directory)%(filename)%(extension)')"/>
        <Message Text="identity: @(Schema->'%(identity)')"/>
        <Message Text="filename: @(Schema->'%(filename)')"/>
        <Message Text="directory: @(Schema->'%(directory)')"/>
        <Message Text="relativedir: @(Schema->'%(relativedir)')"/>
        <Message Text="extension: @(Schema->'%(extension)')"/>
    </Target>
</Project>
```

### <a name="comments"></a>Komentarze

 Ten przykład generuje następujące wyniki:

```
rootdir: C:\
fullpath: C:\sub0\sub1\sub2\sub3\myfile.xsd
rootdir + directory + filename + extension: C:\sub0\sub1\sub2\sub3\myfile.xsd
identity: sub1\sub2\sub3\myfile.xsd
filename: myfile
directory: sub0\sub1\sub2\sub3\
relativedir: sub1\sub2\sub3\
extension: .xsd
```

## <a name="see-also"></a>Zobacz też

- [Pojęcia dotyczące programu MSBuild](../msbuild/msbuild-concepts.md)
- [Dokumentacja programu MSBuild](../msbuild/msbuild-reference.md)
- [Instrukcje: kompilowanie przyrostowe](../msbuild/how-to-build-incrementally.md)
