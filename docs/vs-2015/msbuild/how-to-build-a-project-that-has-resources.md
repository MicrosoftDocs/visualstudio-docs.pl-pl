---
title: 'Instrukcje: kompilowanie projektu zawierającego zasoby | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
ms.topic: conceptual
helpviewer_keywords:
- resource files, compiling with MSBuild
- resources [Visual Studio], compiling with MSBuild
- projects [.NET Framework], building
- MSBuild, building a project with resources
ms.assetid: d07ac73f-2c2d-4e9a-812a-6dcb632bafe2
caps.latest.revision: 17
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: fb77db891e824f5f2900ef191049e65cb2c89a98
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "65686518"
---
# <a name="how-to-build-a-project-that-has-resources"></a>Porady: kompilacja projektu zawierającego zasoby
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Jeśli tworzysz zlokalizowane wersje projektu, wszystkie elementy interfejsu użytkownika muszą być rozdzielone na pliki zasobów dla różnych języków. Jeśli projekt używa tylko ciągów, pliki zasobów mogą używać plików tekstowych. Alternatywnie możesz użyć plików. resx jako plików zasobów.  
  
## <a name="compiling-resources-with-msbuild"></a>Kompilowanie zasobów przy użyciu programu MSBuild  
 Biblioteka typowych zadań, które są dostarczane z programem [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] , zawiera `GenerateResource` zadanie, którego można użyć do kompilowania zasobów w plikach resx lub tekstowych. To zadanie zawiera `Sources` parametr służący do określania, które pliki zasobów do skompilowania, i `OutputResources` parametru, aby określić nazwy dla plików zasobów wyjściowych. Aby uzyskać więcej informacji o `GenerateResource` zadaniu, zobacz [GenerateResource Task](../msbuild/generateresource-task.md).  
  
#### <a name="to-compile-resources-with-msbuild"></a>Aby skompilować zasoby przy użyciu programu MSBuild  
  
1. Zidentyfikuj pliki zasobów projektu i przekaż je do `GenerateResource` zadania, jako listy elementów lub jako nazwy plików.  
  
2. Określ `OutputResources` parametr `GenerateResource` zadania, który pozwala ustawić nazwy dla plików zasobów wyjściowych.  
  
3. Użyj `Output` elementu zadania do przechowywania wartości `OutputResources` parametru w elemencie.  
  
4. Użyj elementu utworzonego na podstawie `Output` elementu jako dane wejściowe w innym zadaniu.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład kodu pokazuje `Output` , jak element określa, że `OutputResources` atrybut `GenerateResource` zadania będzie zawierać skompilowane pliki zasobów `alpha.resources` i `beta.resources` czy te dwa pliki zostaną umieszczone wewnątrz `Resources` listy elementów. Identyfikując te pliki. resources jako kolekcję elementów o tej samej nazwie, można je łatwo wykorzystać jako dane wejściowe dla innego zadania, na przykład zadanie [CSC](../msbuild/csc-task.md) .  
  
 To zadanie jest równoważne użyciu przełącznika **/Compile** dla [Resgen.exe](https://msdn.microsoft.com/library/8ef159de-b660-4bec-9213-c3fbc4d1c6f4):  
  
 `Resgen.exe /compile alpha.resx,alpha.resources /compile beta.txt,beta.resources`  
  
```  
<GenerateResource  
    Sources="alpha.resx; beta.txt"  
    OutputResources="alpha.resources; beta.resources">  
    <Output TaskParameter="OutputResources"  
        ItemName="Resources"/>  
</GenerateResource>  
```  
  
## <a name="example"></a>Przykład  
 Następujący przykładowy projekt zawiera dwa zadania: `GenerateResource` zadanie do kompilowania zasobów i `Csc` zadania w celu skompilowania zarówno plików kodu źródłowego, jak i skompilowanych plików zasobów. Pliki zasobów skompilowane przez `GenerateResource` zadanie są przechowywane w `Resources` elemencie i przesyłane do `Csc` zadania.  
  
```  
<Project DefaultTargets = "Build"  
    xmlns="http://schemas.microsoft.com/developer/msbuild/2003" >  
  
    <Target Name="Resources">  
        <GenerateResource  
            Sources="alpha.resx; beta.txt"  
            OutputResources="alpha.resources; beta.resources">  
            <Output TaskParameter="OutputResources"  
                ItemName="Resources"/>  
        </GenerateResource>  
    </Target>  
  
    <Target Name="Build" DependsOnTargets="Resources">  
        <Csc Sources="hello.cs"  
                Resources="@(Resources)"  
                OutputAssembly="hello.exe"/>  
    </Target>  
</Project>  
```  
  
## <a name="see-also"></a>Zobacz też  
[MSBuild](msbuild.md)  
 [GenerateResource, zadanie](../msbuild/generateresource-task.md)   
 [CSC — zadanie](../msbuild/csc-task.md)   
 [Resgen.exe (Generator plików zasobów)](https://msdn.microsoft.com/library/8ef159de-b660-4bec-9213-c3fbc4d1c6f4)
