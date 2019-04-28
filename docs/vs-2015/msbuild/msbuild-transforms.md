---
title: Przekształcenia w programie MSBuild | Dokumentacja firmy Microsoft
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
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "63426036"
---
# <a name="msbuild-transforms"></a>Przekształcenia w programie MSBuild
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Transformacja jest konwersją jeden do jednego jeden element listy do innej. Oprócz włączenia projektu można przekonwertować listy elementów, przekształcenia umożliwia docelowego w celu identyfikowania bezpośrednie mapowanie między ich dane wejściowe i wyjściowe. W tym temacie opisano przekształceń i w jaki sposób [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] są one używane do kompilowania projektów wydajniej.  
  
## <a name="transform-modifiers"></a>Przekształcanie modyfikatorów  
 Przekształcenia nie dowolnego, ale są ograniczone dzięki specjalnej składni, w którym wszystkie przekształcenia Modyfikatory musi być w formacie %(*ItemMetaDataName*). Wszystkie metadane elementu może służyć jako modyfikator transformacji. W tym metadane dobrze znanego elementu, który jest przypisany do każdego elementu po jego utworzeniu. Aby uzyskać listę metadane dobrze znanego elementu, zobacz [metadane dobrze znanego elementu](../msbuild/msbuild-well-known-item-metadata.md).  
  
 W poniższym przykładzie lista plików resx jest przekształcana na listę plików Resources. Modyfikator przekształcenie %(filename) określa, czy każdego pliku Resources ma taką samą nazwę jak odpowiadający mu plik Resx.  
  
```  
@(RESXFile->'%(filename).resources')  
```  
  
> [!NOTE]
> Można określić niestandardowe separatora listy elementów przekształcone w taki sam sposób określ separatora listy standardowych elementów. Na przykład aby rozdzielić listę elementów przekształcony za pomocą przecinka (,) zamiast domyślnej średnika (;), należy użyć następujący kod XML.  
  
```  
@(RESXFile->'Toolset\%(filename)%(extension)', ',')  
```  
  
 Na przykład, jeśli elementy na liście elementu @(RESXFile) `Form1.resx`, `Form2.resx`, i `Form3.resx`, będą dane wyjściowe na liście po przekształceniu `Form1.resources`, `Form2.resources`, i `Form3.resources`.  
  
## <a name="using-multiple-modifiers"></a>Za pomocą wielu modyfikatorów  
 Wyrażenie przekształcania może zawierać wiele modyfikatorów, których można łączyć w dowolnej kolejności i można powtarzać. W poniższym przykładzie nazwę katalogu, który zawiera pliki jest zmieniany, ale pliki zachować oryginalne rozszerzenie nazwy i pliku nazwy.  
  
```  
@(RESXFile->'Toolset\%(filename)%(extension)')  
```  
  
 Na przykład, jeśli elementy, które są zawarte w `RESXFile` są listy elementów `Project1\Form1.resx`, `Project1\Form2.resx`, i `Project1\Form3.text`, będą dane wyjściowe na liście po przekształceniu `Toolset\Form1.resx`, `Toolset\Form2.resx`, i `Toolset\Form3.text`.  
  
## <a name="dependency-analysis"></a>Analiza zależności  
 Przekształcenia gwarantuje mapowanie jeden do jednego między listy elementów przekształcone i oryginalnej listy elementów. W związku z tym, jeśli obiekt docelowy tworzy dane wyjściowe, które są przekształcenia danych wejściowych, [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] można analizować sygnatury czasowe z wejściami i wyjściami i zdecyduj, czy chcesz pominąć, tworzenie lub częściowo odbudować obiektu docelowego.  
  
 W [zadanie kopiowania](../msbuild/copy-task.md) w poniższym przykładzie każdy plik w `BuiltAssemblies` listy elementów mapy do pliku w folderze docelowym zadania określone za pomocą przekształcenia w `Outputs` atrybutu. Jeśli plik w `BuiltAssemblies` elementu Lista zmian `Copy` zadanie będzie uruchamiane tylko w przypadku zmienionego pliku i wszystkie inne pliki zostaną pominięte. Aby uzyskać więcej informacji na temat analizy zależności oraz jak użyć przekształceń, zobacz [jak: Kompilacja przyrostowa](../msbuild/how-to-build-incrementally.md).  
  
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
 W poniższym przykładzie przedstawiono [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] pliku projektu, który używa przekształcenia. W tym przykładzie przyjęto założenie, że istnieje tylko jeden plik XSD w katalogu c:\sub0\sub1\sub2\sub3 i że katalog roboczy jest c:\sub0.  
  
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
 [Odwołanie do narzędzia MSBuild](../msbuild/msbuild-reference.md)   
 [Instrukcje: kompilacja przyrostowa](../msbuild/how-to-build-incrementally.md)
