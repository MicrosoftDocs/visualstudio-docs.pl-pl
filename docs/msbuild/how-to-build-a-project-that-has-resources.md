---
title: 'Instrukcje: kompilowanie projektu zawierającego zasoby | Microsoft Docs'
description: Dowiedz się więcej na temat sposobu tworzenia projektu zawierającego zasoby oraz sposobu kompilowania zasobów przy użyciu programu MSBuild.
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 195ef17e4770d7050bc3b10f11ca5530e5ca49cc
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99914475"
---
# <a name="how-to-build-a-project-that-has-resources"></a>Instrukcje: kompilowanie projektu zawierającego zasoby

Jeśli tworzysz zlokalizowane wersje projektu, wszystkie elementy interfejsu użytkownika muszą być rozdzielone na pliki zasobów dla różnych języków. Jeśli projekt używa tylko ciągów, pliki zasobów mogą używać plików tekstowych. Alternatywnie możesz użyć plików *. resx* jako plików zasobów.

## <a name="compile-resources-with-msbuild"></a>Kompilowanie zasobów przy użyciu programu MSBuild

Biblioteka typowych zadań, które są dostarczane z programem MSBuild, zawiera `GenerateResource` zadanie, którego można użyć do kompilowania zasobów w plikach *resx* lub tekstowych. To zadanie zawiera `Sources` parametr służący do określania, które pliki zasobów do skompilowania, i `OutputResources` parametru, aby określić nazwy dla plików zasobów wyjściowych. Aby uzyskać więcej informacji o `GenerateResource` zadaniu, zobacz [GenerateResource Task](../msbuild/generateresource-task.md).

#### <a name="to-compile-resources-with-msbuild"></a>Aby skompilować zasoby przy użyciu programu MSBuild

1. Zidentyfikuj pliki zasobów projektu i przekaż je do `GenerateResource` zadania, jako listy elementów lub jako nazwy plików.

2. Określ `OutputResources` parametr `GenerateResource` zadania, który pozwala ustawić nazwy dla plików zasobów wyjściowych.

3. Użyj `Output` elementu zadania do przechowywania wartości `OutputResources` parametru w elemencie.

4. Użyj elementu utworzonego na podstawie `Output` elementu jako dane wejściowe w innym zadaniu.

## <a name="example-1"></a>Przykład 1

Poniższy przykład kodu pokazuje `Output` , jak element określa, że `OutputResources` atrybut `GenerateResource` zadania będzie zawierać skompilowane pliki zasobów *Alpha. resources* i *beta. resources* oraz że te dwa pliki zostaną umieszczone wewnątrz `Resources` listy elementów. Identyfikując te pliki *. resources* jako kolekcję elementów o tej samej nazwie, można je łatwo wykorzystać jako dane wejściowe dla innego zadania, na przykład zadanie [CSC](../msbuild/csc-task.md) .

To zadanie jest równoważne użyciu przełącznika **/Compile** dla [Resgen.exe](/dotnet/framework/tools/resgen-exe-resource-file-generator):

`Resgen.exe /compile alpha.resx,alpha.resources /compile beta.txt,beta.resources`

```xml
<GenerateResource
    Sources="alpha.resx; beta.txt"
    OutputResources="alpha.resources; beta.resources">
    <Output TaskParameter="OutputResources"
        ItemName="Resources"/>
</GenerateResource>
```

## <a name="example-2"></a>Przykład 2

Następujący przykładowy projekt zawiera dwa zadania: `GenerateResource` zadanie do kompilowania zasobów i `Csc` zadania w celu skompilowania zarówno plików kodu źródłowego, jak i skompilowanych plików zasobów. Pliki zasobów skompilowane przez `GenerateResource` zadanie są przechowywane w `Resources` elemencie i przesyłane do `Csc` zadania.

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
- [GenerateResource — zadanie](../msbuild/generateresource-task.md)
- [Csc — Zadanie](../msbuild/csc-task.md)
- [Resgen.exe (Generator plików zasobów)](/dotnet/framework/tools/resgen-exe-resource-file-generator)
