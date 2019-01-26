---
title: 'Instrukcje: Skompiluj projekt, który ma zasoby | Dokumentacja firmy Microsoft'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- resource files, compiling with MSBuild
- resources [Visual Studio], compiling with MSBuild
- projects [.NET Framework], building
- MSBuild, building a project with resources
ms.assetid: d07ac73f-2c2d-4e9a-812a-6dcb632bafe2
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 8886f4970a4888d72f0c0f919069c10658e92332
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/25/2019
ms.locfileid: "54948963"
---
# <a name="how-to-build-a-project-that-has-resources"></a>Instrukcje: Kompilacja projektu zawierającego zasoby
Jeśli tworzysz zlokalizowane wersje projektu, wszystkich elementów interfejsu użytkownika muszą być oddzielone do plików zasobów w różnych językach. Jeśli projekt używa tylko ciągi, pliki zasobów, można użyć plików tekstowych. Alternatywnie, można użyć *resx* pliki jako pliki zasobów.  
  
## <a name="compile-resources-with-msbuild"></a>Kompilowanie zasobów za pomocą narzędzia MSBuild  
 Biblioteka typowych zadań, które jest dostarczane z [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] obejmuje `GenerateResource` zadanie, które można użyć do skompilowania zasobów albo *resx* lub pliki tekstowe. To zadanie obejmuje `Sources` parametru do określenia, który zasób plików do kompilacji i `OutputResources` parametru do określenia nazwy plików zasobów danych wyjściowych. Aby uzyskać więcej informacji na temat `GenerateResource` zadań, zobacz [generateresource — zadanie](../msbuild/generateresource-task.md).  
  
#### <a name="to-compile-resources-with-msbuild"></a>Aby skompilować zasobów za pomocą narzędzia MSBuild  
  
1.  Identyfikowanie plików zasobów projektu i przekazywać je do `GenerateResource` zadania, w postaci listy elementów lub jako nazwy plików.  
  
2.  Określ `OutputResources` parametru `GenerateResource` zadania, które można ustawić nazwy plików zasobów danych wyjściowych.  
  
3.  Użyj `Output` element zadania do przechowywania wartości `OutputResources` parametr w elemencie.  
  
4.  Przy użyciu utworzonego na podstawie `Output` elementu jako dane wejściowe do innego zadania.  
  
## <a name="example"></a>Przykład  
 Poniższy kod przedstawia przykład sposób, w jaki `Output` elementu Określa, że `OutputResources` atrybutu `GenerateResource` zadanie będzie zawierać pliki skompilowane zasobów *alpha.resources* i  *beta.resources* oraz że te dwa pliki zostaną umieszczone wewnątrz `Resources` listy elementów. Identyfikując te *Resources* pliki jako kolekcja elementów o takiej samej nazwie, łatwo można je jako dane wejściowe innego zadania, takie jak [Csc](../msbuild/csc-task.md) zadania.  
  
 To zadanie jest równoważne użyciu **/compile** przełączać [Resgen.exe](/dotnet/framework/tools/resgen-exe-resource-file-generator):  
  
 `Resgen.exe /compile alpha.resx,alpha.resources /compile beta.txt,beta.resources`  
  
```xml  
<GenerateResource  
    Sources="alpha.resx; beta.txt"  
    OutputResources="alpha.resources; beta.resources">  
    <Output TaskParameter="OutputResources"  
        ItemName="Resources"/>  
</GenerateResource>  
```  
  
## <a name="example"></a>Przykład  
 Poniższy przykładowy projekt zawiera dwa zadania: `GenerateResource` zadanie, aby skompilować zasobów i `Csc` zadania do kompilowania plików kodu źródłowego i pliki zasobów skompilowany. Pliki zasobów opracowane przez `GenerateResource` zadania są przechowywane w `Resources` elementu i przekazywane do `Csc` zadania.  
  
```xml  
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
  
## <a name="see-also"></a>Zobacz także  
[MSBuild](../msbuild/msbuild.md)  
 [Generateresource — zadanie](../msbuild/generateresource-task.md)   
 [CSC — zadanie](../msbuild/csc-task.md)   
 [Resgen.exe (generator pliku zasobów)](/dotnet/framework/tools/resgen-exe-resource-file-generator)