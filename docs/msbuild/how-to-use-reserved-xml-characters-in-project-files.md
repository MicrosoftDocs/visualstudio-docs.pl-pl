---
title: 'Instrukcje: Użycie znaków zarezerwowanych XML w plikach projektu | Dokumentacja firmy Microsoft'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- MSBuild, using reserved XML characters
- MSBuild, reserved XML characters
ms.assetid: 1ae37275-96bf-4e6e-897b-6b048e5bbe93
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 02c5693a2edca0d81e21e73215e00f25aae939eb
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/21/2019
ms.locfileid: "56603874"
---
# <a name="how-to-use-reserved-xml-characters-in-project-files"></a>Instrukcje: Użycie znaków zarezerwowanych XML w plikach projektu
Podczas tworzenia plików projektu, może być konieczne użycie zarezerwowanych znaków XML w przypadku, na przykład w wartości właściwości lub wartości parametrów zadania. Jednak niektóre zastrzeżone znaki muszą zostać zastąpione nazwanych jednostek, dzięki czemu można przeanalizować pliku projektu.

## <a name="use-reserved-characters"></a>Zastrzeżone znaki
 W poniższej tabeli opisano zarezerwowanych znaków XML, które muszą zostać zastąpione odpowiednia jednostka o nazwie, dzięki czemu można przeanalizować pliku projektu.

|Zastrzeżonego znaku|Nazwanych jednostek|
|------------------------|------------------|
|\<|&amp;lt;|
|>|&amp;gt;|
|&|&amp;amp;|
|"|&amp;quot;|
|'|&amp;APOS;|

#### <a name="to-use-double-quotes-in-a-project-file"></a>Aby używać cudzysłowów w pliku projektu

-   Zamień podwójnych cudzysłowów odpowiadającą nazwie podmiotu, &amp;quot;. Na przykład, aby umieścić podwójnego cudzysłowu wokół `EXEFile` listy elementów, wpisz:

    ```xml
    <Message Text="The output file is &quot;@(EXEFile)&quot;."/>
    ```

## <a name="example"></a>Przykład
 W poniższym przykładzie kodu podwójne cudzysłowy są używane do zaznacz nazwę pliku na komunikat, który jest wysyłany przy użyciu pliku projektu.

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

## <a name="see-also"></a>Zobacz także
- [Odwołanie do narzędzia MSBuild](../msbuild/msbuild-reference.md)
- [MSBuild](../msbuild/msbuild.md)
