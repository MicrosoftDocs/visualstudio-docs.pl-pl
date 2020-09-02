---
title: 'Instrukcje: kompilowanie przyrostowe | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
ms.topic: conceptual
helpviewer_keywords:
- MSBuild, incremental builds
- incremental builds
- MSBuild, building incrementally
ms.assetid: 8d82d7d8-a2f1-4df6-9d2f-80b9e0cb3ac3
caps.latest.revision: 24
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: c4b2e6dd825cfcf67ffffd9ace27017c8d01aa33
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "64835885"
---
# <a name="how-to-build-incrementally"></a>Porady: kompilacja przyrostowa
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Podczas kompilowania dużego projektu ważne jest, aby wcześniej skompilowane składniki, które są nadal aktualne, nie zostały odbudowane. Jeśli wszystkie elementy docelowe są tworzone za każdym razem, ukończenie każdej kompilacji potrwa dużo czasu. Aby włączyć Kompilacje przyrostowe (kompilacje, w których tylko te elementy docelowe, które nie zostały skompilowane przed lub celem, które są nieaktualne, są ponownie kompilowane), [!INCLUDE[vstecmsbuildengine](../includes/vstecmsbuildengine-md.md)] ( [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] ) mogą porównać sygnatury czasowe plików wejściowych z sygnaturami czasowymi plików wyjściowych i określić, czy pominąć, skompilować lub częściowo odbudować element docelowy. Jednak musi istnieć mapowanie jeden do jednego między danymi wejściowymi i wyjściowymi. Można użyć transformacji, aby umożliwić obiektom docelowym zidentyfikowanie tego bezpośredniego mapowania. Aby uzyskać więcej informacji na temat transformacji, zobacz [transformacje](../msbuild/msbuild-transforms.md).  
  
## <a name="specifying-inputs-and-outputs"></a>Określanie danych wejściowych i wyjściowych  
 Element docelowy można skompilować przyrostowo, jeśli dane wejściowe i wyjściowe są określone w pliku projektu.  
  
#### <a name="to-specify-inputs-and-outputs-for-a-target"></a>Aby określić dane wejściowe i wyjściowe dla elementu docelowego  
  
- Użyj `Inputs` atrybutów i `Outputs` `Target` elementu. Na przykład:  
  
  ```  
  <Target Name="Build"  
      Inputs="@(CSFile)"  
      Outputs="hello.exe">  
  ```  
  
  [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] można porównać sygnatury czasowe plików wejściowych z sygnaturami czasowymi plików wyjściowych i określić, czy pominąć, skompilować lub częściowo ponownie skompilować element docelowy. W poniższym przykładzie, jeśli dowolny plik na `@(CSFile)` liście elementów jest nowszy niż plik hello.exe, program uruchomi [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] element docelowy; w przeciwnym razie zostanie pominięty:  
  
```  
<Target Name="Build"   
    Inputs="@(CSFile)"   
    Outputs="hello.exe">  
  
    <Csc  
        Sources="@(CSFile)"   
        OutputAssembly="hello.exe"/>  
</Target>  
```  
  
 Gdy dane wejściowe i wyjściowe są określone w elemencie docelowym, wszystkie dane wyjściowe można mapować tylko na jedną wartość wejściową lub nie może istnieć bezpośrednie mapowanie między wyjściem i danymi wejściowymi. W poprzednim [zadaniu CSC](../msbuild/csc-task.md), na przykład dane wyjściowe hello.exe, nie mogą zostać zamapowane na żadne pojedyncze dane wejściowe — zależy to od wszystkich z nich.  
  
> [!NOTE]
> Obiekt docelowy, w którym nie istnieje bezpośrednie mapowanie między wejściami i wyjściami, zawsze kompiluje się częściej niż obiekt docelowy, w którym każde dane wyjściowe można mapować tylko na jedną wartość wejściową, ponieważ [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] nie można określić, które wyjścia muszą zostać odbudowane, jeśli niektóre dane wejściowe uległy zmianie.  
  
 Zadania, w których można zidentyfikować bezpośrednie mapowanie między wynikami i danymi wejściowymi, takie jak [zadanie LC](../msbuild/lc-task.md), są najbardziej odpowiednie dla kompilacji przyrostowych, w przeciwieństwie do zadań, takich jak `Csc` i [VBC](../msbuild/vbc-task.md), które tworzą jeden zestaw wyjściowy z wielu danych wejściowych.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie używa się projektu, który kompiluje pliki pomocy dla hipotetycznego systemu pomocy. Projekt działa przez konwertowanie źródłowych plików txt na pośrednie pliki zawartości, które następnie są łączone z plikami metadanych XML w celu utworzenia końcowego pliku pomocy używanego przez system pomocy. Projekt używa następujących hipotetycznych zadań:  
  
- `GenerateContentFiles`: Konwertuje pliki txt na pliki zawartości.  
  
- `BuildHelp`: Łączy pliki zawartości i pliki metadanych XML, aby skompilować końcowy plik pomocy.  
  
  Projekt używa transformacji, aby utworzyć mapowanie jeden do jednego między danymi wejściowymi i wyjściowymi w `GenerateContentFiles` zadaniu. Aby uzyskać więcej informacji, zobacz [transformacje](../msbuild/msbuild-transforms.md). Ponadto `Output` element jest ustawiony do automatycznego używania danych wyjściowych z `GenerateContentFiles` zadania jako dane wejściowe dla `BuildHelp` zadania.  
  
  Ten plik projektu zawiera `Convert` `Build` elementy i. `GenerateContentFiles`Zadania i `BuildHelp` są umieszczane w `Convert` i `Build` obiekty docelowe odpowiednio w taki sposób, że każdy element docelowy może być zbudowany przyrostowo. Za pomocą `Output` elementu dane wyjściowe `GenerateContentFiles` zadania są umieszczane na `ContentFile` liście elementów, gdzie mogą być używane jako dane wejściowe `BuildHelp` zadania. Użycie `Output` elementu w ten sposób automatycznie udostępnia dane wyjściowe z jednego zadania jako dane wejściowe dla innego zadania, dzięki czemu nie trzeba ręcznie wyświetlać poszczególnych elementów lub list elementów w każdym zadaniu.  
  
> [!NOTE]
> Mimo że `GenerateContentFiles` element docelowy może kompilować przyrostowo, wszystkie dane wyjściowe z tego obiektu docelowego zawsze są wymagane jako wejścia dla `BuildHelp` elementu docelowego. [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] automatycznie udostępnia wszystkie dane wyjściowe z jednego obiektu docelowego jako dane wejściowe dla innego obiektu docelowego przy użyciu `Output` elementu.  
  
```  
<Project DefaultTargets="Build"  
    xmlns="http://schemas.microsoft.com/developer/msbuild/2003" >  
  
    <ItemGroup>  
        <TXTFile Include="*.txt"/>  
        <XMLFile Include="\metadata\*.xml"/>  
    </ItemGroup>  
  
    <Target Name = "Convert"  
        Inputs="@(TXTFile)"  
        Outputs="@(TXTFile->'%(Filename).content')">  
  
        <GenerateContentFiles  
            Sources = "@(TXTFile)">  
            <Output TaskParameter = "OutputContentFiles"  
                ItemName = "ContentFiles"/>  
        </GenerateContentFiles>  
    </Target>  
  
    <Target Name = "Build" DependsOnTargets = "Convert"  
        Inputs="@(ContentFiles);@(XMLFiles)"  
        Outputs="$(MSBuildProjectName).help">  
  
        <BuildHelp  
            ContentFiles = "@(ContentFiles)"  
            MetadataFiles = "@(XMLFile)"  
            OutputFileName = "$(MSBuildProjectName).help"/>  
    </Target>  
</Project>  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Celach](../msbuild/msbuild-targets.md)   
 [Target — element (MSBuild)](../msbuild/target-element-msbuild.md)   
 [Przekształca](../msbuild/msbuild-transforms.md)   
 [CSC — zadanie](../msbuild/csc-task.md)   
 [VBC, zadanie](../msbuild/vbc-task.md)
