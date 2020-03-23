---
title: Transformacje MSBuild | Dokumenty firmy Microsoft
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
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "77633112"
---
# <a name="msbuild-transforms"></a>Transformacja MSBuild

Transformacja to konwersja jeden do jednego z listy elementów na inną. Oprócz włączania projektu do konwersji list towarów, transformacja umożliwia miejsce docelowe do identyfikowania bezpośredniego mapowania między jego danych wejściowych i wyjściowych. W tym temacie wyjaśniono przekształcenia i jak MSBuild używa ich do tworzenia projektów bardziej efektywnie.

## <a name="transform-modifiers"></a>Modyfikatory przekształcania

Przekształcenia nie są dowolne, ale są ograniczone przez specjalną składnię,\<w której wszystkie modyfikatory przekształcania muszą być w formacie %( ItemMetaDataName>). Wszystkie metadane elementu mogą służyć jako modyfikator transformacji. Obejmuje to dobrze znane metadane elementu, który jest przypisany do każdego elementu podczas jego tworzenia. Aby uzyskać listę dobrze znanych metadanych elementu, zobacz [Metadane znanego elementu](../msbuild/msbuild-well-known-item-metadata.md).

W poniższym przykładzie lista plików *resx* jest przekształcana w listę plików *.resources.* Modyfikator transformacji %(nazwa pliku) określa, że każdy plik *.resources* ma taką samą nazwę pliku jak odpowiedni plik *.resx.*

```xml
@(RESXFile->'%(filename).resources')
```

Jeśli na przykład elementami na liście elementów @(RESXFile) są *form1.resx,* *Form2.resx*i *Form3.resx*, dane wyjściowe na przekształconej liście będą *form1.resources*, *Form2.resources*i *Form3.resources*.

> [!NOTE]
> Separator niestandardowy dla listy przekształconych elementów można określić w taki sam sposób, jak separator dla standardowej listy elementów. Na przykład, aby oddzielić listę przekształconych elementów przy użyciu przecinka (,) zamiast domyślnego średnika (;), użyj następującego kodu XML:`@(RESXFile->'Toolset\%(filename)%(extension)', ',')`

## <a name="use-multiple-modifiers"></a>Używanie wielu modyfikatorów

 Wyrażenie przekształcania może zawierać wiele modyfikatorów, które można łączyć w dowolnej kolejności i mogą być powtarzane. W poniższym przykładzie nazwa katalogu zawierającego pliki zostanie zmieniona, ale pliki zachowują oryginalną nazwę i rozszerzenie nazwy pliku.

```xml
@(RESXFile->'Toolset\%(filename)%(extension)')
```

 Jeśli na przykład elementami znajdującymi `RESXFile` się na liście elementów są *Project1\Form1.resx*, *Project1\Form2.resx*i *Project1\Form3.text*, dane wyjściowe na przekształconej liście będą *zawierały zestaw narzędzi Toolset\Form1.resx*, *Zestaw narzędzi\Form2.resx*i *Zestaw narzędziowy\Form3.text*.

## <a name="dependency-analysis"></a>Analiza zależności

 Transformacje gwarantują mapowanie jeden do jednego między przekształconą listą elementów a oryginalną listą elementów. W związku z tym jeśli obiekt docelowy tworzy dane wyjściowe, które są przekształcenia danych wejściowych, MSBuild można analizować sygnatury czasowe danych wejściowych i wyjściowych i zdecydować, czy pominąć, skompilować lub częściowo odbudować obiekt docelowy.

 W [zadaniu Kopiuj](../msbuild/copy-task.md) w poniższym przykładzie każdy plik na liście `BuiltAssemblies` elementów jest mapowana `Outputs` do pliku w folderze docelowym zadania, określonego przy użyciu przekształcenia w atrybucie. Jeśli plik na `BuiltAssemblies` liście elementów `Copy` ulegnie zmianie, zadanie zostanie uruchamiane tylko dla zmienionego pliku, a wszystkie inne pliki zostaną pominięte. Aby uzyskać więcej informacji na temat analizy zależności i sposobu korzystania z przekształceń, zobacz [Jak: Tworzenie przyrostowo](../msbuild/how-to-build-incrementally.md).

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

 W poniższym przykładzie przedstawiono plik projektu MSBuild, który używa przekształceń. W tym przykładzie założono, że w katalogu *c:\sub0\sub1\sub3* znajduje się tylko jeden plik *xsd,* a katalog roboczy to *c:\sub0*.

### <a name="code"></a>Code

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

- [Koncepcje MSBuild](../msbuild/msbuild-concepts.md)
- [Odwołanie do budynku MSBuild](../msbuild/msbuild-reference.md)
- [Jak: Tworzenie przyrostowo](../msbuild/how-to-build-incrementally.md)
