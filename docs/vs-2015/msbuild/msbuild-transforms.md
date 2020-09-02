---
title: Przekształcenia programu MSBuild | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
ms.topic: reference
helpviewer_keywords:
- MSBuild, transforms
- transforms [MSBuild]
ms.assetid: d0bcfc3c-14fa-455e-805c-63ccffa4a3bf
caps.latest.revision: 16
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 3f9a6f7985e3ebb3e77dcc605157f75e00a0842b
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "64793902"
---
# <a name="msbuild-transforms"></a>Przekształcenia w programie MSBuild
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Transformacja jest konwersją jeden do jednego z jednej listy elementów na inną. Poza umożliwieniem projektowi konwersji list elementów, transformacja umożliwia obiektowi docelowemu znalezienie bezpośredniego mapowania między danymi wejściowymi i wyjściowymi. W tym temacie objaśniono transformacje i jak program [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] używa ich do bardziej wydajnego kompilowania projektów.  
  
## <a name="transform-modifiers"></a>Przekształć Modyfikatory  
 Przekształcenia nie są dowolne, ale są ograniczone przez specjalną składnię, w której wszystkie Modyfikatory transformacji muszą mieć format%(*ItemMetaDataName*). Wszystkie metadane elementu mogą być używane jako modyfikator przekształcania. Obejmuje to metadane dobrze znanego elementu, które są przypisywane do każdego elementu podczas jego tworzenia. Aby uzyskać listę dobrze znanych metadanych elementu, zobacz [dobrze znane metadane elementu](../msbuild/msbuild-well-known-item-metadata.md).  
  
 W poniższym przykładzie lista plików resx jest przekształcana na listę plików Resources. Modyfikator przekształcenia% (filename) określa, że każdy plik resources ma taką samą nazwę jak plik. resx.  
  
```  
@(RESXFile->'%(filename).resources')  
```  
  
> [!NOTE]
> Możesz określić niestandardowy separator dla listy przekształconych elementów w ten sam sposób, w jaki określisz separator dla standardowej listy elementów. Na przykład, aby oddzielić listę przekształconych elementów przy użyciu przecinka (,) zamiast domyślnego średnika (;), użyj poniższego kodu XML.  
  
```  
@(RESXFile->'Toolset\%(filename)%(extension)', ',')  
```  
  
 Na przykład, jeśli elementy na liście elementów @ (RESXFile) to `Form1.resx` , `Form2.resx` , i `Form3.resx` , dane wyjściowe z przekształconej listy będą `Form1.resources` , `Form2.resources` i `Form3.resources` .  
  
## <a name="using-multiple-modifiers"></a>Używanie wielu modyfikatorów  
 Wyrażenie przekształcenia może zawierać wiele modyfikatorów, które mogą być połączone w dowolnej kolejności i mogą być powtarzane. W poniższym przykładzie nazwa katalogu zawierającego pliki jest zmieniana, ale pliki zachowują oryginalną nazwę i rozszerzenie nazwy pliku.  
  
```  
@(RESXFile->'Toolset\%(filename)%(extension)')  
```  
  
 Na przykład, jeśli elementy, które znajdują się na `RESXFile` liście elementów są `Project1\Form1.resx` , `Project1\Form2.resx` , i `Project1\Form3.text` , dane wyjściowe z przekształconej listy będą `Toolset\Form1.resx` , `Toolset\Form2.resx` i `Toolset\Form3.text` .  
  
## <a name="dependency-analysis"></a>Analiza zależności  
 Transformacje gwarantują mapowanie jeden do jednego między listą przekształconych elementów a listą pierwotnych elementów. W związku z tym, jeśli obiekt docelowy tworzy wyjścia, które są przekształcane dane wejściowe, [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] może analizować sygnatury czasowe wejść i wyjść oraz decydować, czy pominąć, skompilować lub częściowo skompilować element docelowy.  
  
 W [zadaniu Copy](../msbuild/copy-task.md) w poniższym przykładzie każdy plik na `BuiltAssemblies` liście elementów jest mapowany do pliku w folderze docelowym zadania, określonym przy użyciu transformacji w `Outputs` atrybucie. Jeśli plik na `BuiltAssemblies` liście elementów ulegnie zmianie, `Copy` zadanie zostanie uruchomione tylko dla zmienionego pliku, a wszystkie pozostałe pliki zostaną pominięte. Aby uzyskać więcej informacji na temat analizy zależności i sposobu używania transformacji, zobacz [How to: build przyrostowo](../msbuild/how-to-build-incrementally.md).  
  
```  
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
 Poniższy przykład pokazuje [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] plik projektu, który używa transformacji. W tym przykładzie przyjęto założenie, że w katalogu c:\sub0\sub1\sub2\sub3 istnieje tylko jeden plik XSD, a katalog roboczy to c:\sub0.  
  
### <a name="code"></a>Kod  
  
```  
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
 Ten przykład generuje następujące dane wyjściowe.  
  
```  
rootdir: C:\  
fullpath: C:\xmake\sub1\sub2\sub3\myfile.xsd  
rootdir + directory + filename + extension: C:\xmake\sub1\sub2\sub3\myfile.xsd  
identity: sub1\sub2\sub3\myfile.xsd  
filename: myfile  
directory: xmake\sub1\sub2\sub3\  
relativedir: sub1\sub2\sub3\  
extension: .xsd  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Pojęcia dotyczące programu MSBuild](../msbuild/msbuild-concepts.md)   
 [Dokumentacja programu MSBuild](../msbuild/msbuild-reference.md)   
 [Instrukcje: Kompilacja przyrostowa](../msbuild/how-to-build-incrementally.md)
