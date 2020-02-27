---
title: 'Instrukcje: kompilowanie projektu zawierającego zasoby | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- resource files, compiling with MSBuild
- resources [Visual Studio], compiling with MSBuild
- projects [.NET Framework], building
- MSBuild, building a project with resources
ms.assetid: d07ac73f-2c2d-4e9a-812a-6dcb632bafe2
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: a76246096eec8779ce331e93f01be5ab791d1cdb
ms.sourcegitcommit: 96737c54162f5fd5c97adef9b2d86ccc660b2135
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/26/2020
ms.locfileid: "77633957"
---
# <a name="how-to-build-a-project-that-has-resources"></a>Instrukcje: kompilowanie projektu zawierającego zasoby

Jeśli tworzysz zlokalizowane wersje projektu, wszystkie elementy interfejsu użytkownika muszą być rozdzielone na pliki zasobów dla różnych języków. Jeśli projekt używa tylko ciągów, pliki zasobów mogą używać plików tekstowych. Alternatywnie możesz użyć plików *. resx* jako plików zasobów.

## <a name="compile-resources-with-msbuild"></a>Kompilowanie zasobów przy użyciu programu MSBuild

Biblioteka typowych zadań, które są dostarczane z programem MSBuild, zawiera zadanie `GenerateResource`, którego można użyć do kompilowania zasobów w plikach *resx* lub plików tekstowych. To zadanie zawiera parametr `Sources`, aby określić, które pliki zasobów należy skompilować, oraz parametr `OutputResources`, aby określić nazwy dla plików zasobów wyjściowych. Aby uzyskać więcej informacji na temat `GenerateResource` zadania, zobacz [zadanie GenerateResource](../msbuild/generateresource-task.md).

#### <a name="to-compile-resources-with-msbuild"></a>Aby skompilować zasoby przy użyciu programu MSBuild

1. Zidentyfikuj pliki zasobów projektu i przekaż je do zadania `GenerateResource`, jako listy elementów lub jako nazwy plików.

2. Określ parametr `OutputResources` zadania `GenerateResource`, które pozwala ustawić nazwy dla plików zasobów wyjściowych.

3. Użyj elementu `Output` zadania do przechowywania wartości parametru `OutputResources` w elemencie.

4. Użyj elementu utworzonego z elementu `Output` jako dane wejściowe w innym zadaniu.

## <a name="example"></a>Przykład

Poniższy przykład kodu pokazuje, jak `Output` element określa, że atrybut `OutputResources` zadania `GenerateResource` będzie zawierać skompilowane pliki zasobów *Alpha. resources* i *beta. resources* oraz że te dwa pliki zostaną umieszczone wewnątrz listy elementów `Resources`. Identyfikując te pliki *. resources* jako kolekcję elementów o tej samej nazwie, można je łatwo wykorzystać jako dane wejściowe dla innego zadania, na przykład zadanie [CSC](../msbuild/csc-task.md) .

To zadanie jest równoważne użyciu przełącznika **/Compile** dla [Resgen. exe](/dotnet/framework/tools/resgen-exe-resource-file-generator):

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

Następujący przykładowy projekt zawiera dwa zadania: zadanie `GenerateResource` do kompilowania zasobów i zadania `Csc` do kompilowania zarówno plików kodu źródłowego, jak i skompilowanych plików zasobów. Pliki zasobów skompilowane przez zadanie `GenerateResource` są przechowywane w elemencie `Resources` i przesyłane do zadania `Csc`.

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

## <a name="see-also"></a>Zobacz też

- [MSBuild](../msbuild/msbuild.md)
- [GenerateResource, zadanie](../msbuild/generateresource-task.md)
- [CSC — zadanie](../msbuild/csc-task.md)
- [Resgen.exe (generator pliku zasobów)](/dotnet/framework/tools/resgen-exe-resource-file-generator)
