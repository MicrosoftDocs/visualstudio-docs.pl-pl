---
title: 'Jak: Tworzenie projektu, który ma zasoby | Dokumenty firmy Microsoft'
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
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "77633957"
---
# <a name="how-to-build-a-project-that-has-resources"></a>Jak: Tworzenie projektu, który ma zasoby

Jeśli budujesz zlokalizowane wersje projektu, wszystkie elementy interfejsu użytkownika muszą być podzielone na pliki zasobów dla różnych języków. Jeśli projekt używa tylko ciągów, pliki zasobów można użyć plików tekstowych. Alternatywnie można użyć plików *resx* jako plików zasobów.

## <a name="compile-resources-with-msbuild"></a>Kompilowanie zasobów za pomocą usługi MSBuild

Biblioteka typowych zadań, która jest dostarczana `GenerateResource` z MSBuild zawiera zadanie, które można użyć do kompilowania zasobów w *plikach .resx lub tekstowych.* To zadanie `Sources` zawiera parametr określający pliki zasobów `OutputResources` do skompilowania oraz parametr określający nazwy plików zasobów wyjściowych. Aby uzyskać więcej `GenerateResource` informacji na temat zadania, zobacz [GenerateResource task](../msbuild/generateresource-task.md).

#### <a name="to-compile-resources-with-msbuild"></a>Aby skompilować zasoby za pomocą usługi MSBuild

1. Zidentyfikuj pliki zasobów projektu `GenerateResource` i przekaż je do zadania, jako listy elementów lub jako nazwy plików.

2. Określ `OutputResources` parametr `GenerateResource` zadania, który umożliwia ustawienie nazw plików zasobów wyjściowych.

3. Użyj `Output` elementu zadania, aby zapisać wartość `OutputResources` parametru w elemencie.

4. Użyj elementu utworzonego `Output` z elementu jako danych wejściowych do innego zadania.

## <a name="example"></a>Przykład

Poniższy przykład kodu `Output` pokazuje, jak `OutputResources` element określa, `GenerateResource` że atrybut zadania będzie zawierać skompilowane pliki zasobów *alpha.resources* i `Resources` *beta.resources* i że te dwa pliki zostaną umieszczone wewnątrz listy elementów. Identyfikując te pliki *.resources* jako zbiór elementów o tej samej nazwie, można łatwo użyć ich jako danych wejściowych dla innego zadania, takiego jak zadanie [Csc.](../msbuild/csc-task.md)

To zadanie jest równoznaczne z użyciem przełącznika **/compile** dla [Resgen.exe:](/dotnet/framework/tools/resgen-exe-resource-file-generator)

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

Poniższy przykładowy projekt zawiera `GenerateResource` dwa zadania: zadanie `Csc` do skompilowania zasobów i zadanie do skompilowania zarówno plików kodu źródłowego, jak i skompilowanych plików zasobów. Pliki zasobów skompilowane przez `GenerateResource` zadanie `Resources` są przechowywane `Csc` w elemencie i przekazywane do zadania.

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

- [Msbuild](../msbuild/msbuild.md)
- [Zadanie GenerateResource](../msbuild/generateresource-task.md)
- [Zadanie csc](../msbuild/csc-task.md)
- [Resgen.exe (generator pliku zasobów)](/dotnet/framework/tools/resgen-exe-resource-file-generator)
