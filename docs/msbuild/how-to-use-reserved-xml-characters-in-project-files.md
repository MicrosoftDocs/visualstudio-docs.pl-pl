---
title: 'Instrukcje: użycie znaków zarezerwowanych XML w plikach projektu | Microsoft Docs'
description: Dowiedz się, jak zastąpić zastrzeżone znaki XML odpowiednimi nazwanymi jednostkami w plikach projektu MSBuild.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- MSBuild, using reserved XML characters
- MSBuild, reserved XML characters
ms.assetid: 1ae37275-96bf-4e6e-897b-6b048e5bbe93
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 64a45bae9665c0c39e9b709cec185f0434f3889b
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99914173"
---
# <a name="how-to-use-reserved-xml-characters-in-project-files"></a>Instrukcje: użycie znaków zarezerwowanych XML w plikach projektu

Podczas tworzenia plików projektu może być konieczne użycie znaków zarezerwowanych XML, na przykład w wartościach właściwości lub w wartościach parametrów zadania. Jednak niektóre zastrzeżone znaki muszą zostać zastąpione przez nazwaną jednostkę, aby można było analizować plik projektu.

## <a name="use-reserved-characters"></a>Użyj znaków zarezerwowanych

 W poniższej tabeli opisano zastrzeżone znaki XML, które muszą zostać zastąpione przez odpowiadającą mu nazwę jednostki, aby można było analizować plik projektu.

|Znak zarezerwowany|Nazwana jednostka|
|------------------------|------------------|
|\<|&amp;przelew|
|>|&amp;gt|
|&|&amp;ograniczony|
|"|&amp;quot;|
|'|&amp;"|

#### <a name="to-use-double-quotes-in-a-project-file"></a>Aby użyć podwójnych cudzysłowów w pliku projektu

- Zamień podwójne cudzysłowy na odpowiadającą nazwaną jednostkę, &amp; quot;. Na przykład, aby umieścić podwójne cudzysłowy wokół `EXEFile` listy elementów, wpisz:

    ```xml
    <Message Text="The output file is &quot;@(EXEFile)&quot;."/>
    ```

## <a name="example"></a>Przykład

 W poniższym przykładzie kodu podwójne cudzysłowy są używane do wyróżnienia nazwy pliku w wiadomości wyjściowej przez plik projektu.

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

- [Dokumentacja programu MSBuild](../msbuild/msbuild-reference.md)
- [MSBuild](../msbuild/msbuild.md)
