---
title: 'Jak: Używanie zastrzeżonych znaków XML w plikach projektu | Dokumenty firmy Microsoft'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- MSBuild, using reserved XML characters
- MSBuild, reserved XML characters
ms.assetid: 1ae37275-96bf-4e6e-897b-6b048e5bbe93
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: a041802af1c2fe8cfa195990e6eda3e9b49d773a
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "77633775"
---
# <a name="how-to-use-reserved-xml-characters-in-project-files"></a>Jak: Używanie zastrzeżonych znaków XML w plikach projektu

Podczas tworzenia plików projektu może być konieczne użycie zastrzeżonych znaków XML, na przykład w wartościach właściwości lub w wartościach parametrów zadania. Jednak niektóre znaki zastrzeżone muszą zostać zastąpione przez nazwaną jednostkę, aby można było przeanalizować plik projektu.

## <a name="use-reserved-characters"></a>Używanie znaków zastrzeżonych

 W poniższej tabeli opisano zastrzeżone znaki XML, które muszą zostać zastąpione przez odpowiednią nazwaną encję, aby można było przeanalizować plik projektu.

|Znak zarezerwowany|Nazwana encja|
|------------------------|------------------|
|\<|&amp;lt;|
|>|&amp;gt;|
|&|&amp;wzmacniacz;|
|"|&amp;quot;|
|'|&amp;apos;|

#### <a name="to-use-double-quotes-in-a-project-file"></a>Aby użyć cudzysłowów w pliku projektu

- Zastąp podwójne cudzysłowy odpowiednią nazwaną encją, &amp;podaj;. Na przykład, aby umieścić podwójne `EXEFile` cudzysłowy wokół listy elementów, wpisz:

    ```xml
    <Message Text="The output file is &quot;@(EXEFile)&quot;."/>
    ```

## <a name="example"></a>Przykład

 W poniższym przykładzie kodu podwójne cudzysłowy są używane do podświetlenia nazwy pliku w komunikacie, który jest wysyłany przez plik projektu.

```xml
<Project DefaultTargets="Compile"
    xmlns="http://schemas.microsoft.com/developer/msbuild/2003" >
    <!-- Set the application name as a property -->
    <PropertyGroup>
        <appname>"HelloWorldCS"</appname>
    </PropertyGroup>
    <!-- Specify the inputs -->
    <ItemGroup>
        <CSFile Include = "consolehwcs1.cs" />
    </ItemGroup>
    <Target Name = "Compile">
        <!-- Run the Visual C# compilation using input
        files of type CSFile -->
        <Csc Sources = "@(CSFile)">
            <!-- Set the OutputAssembly attribute of the CSC task
            to the name of the executable file that is created -->
            <Output
                TaskParameter = "OutputAssembly"
                ItemName = "EXEFile"/>
        </Csc>
        <!-- Log the file name of the output file -->
        <Message Text="The output file is &quot;@(EXEFile)&quot;."/>
    </Target>
</Project>
```

## <a name="see-also"></a>Zobacz też

- [Odwołanie do budynku MSBuild](../msbuild/msbuild-reference.md)
- [Msbuild](../msbuild/msbuild.md)
