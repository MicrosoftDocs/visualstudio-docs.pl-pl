---
title: Odwołanie do nazwy lub lokalizacji pliku projektu
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- locations, referencing
- locations
- MSBuildProjectName property
- MSBuild, referencing the project file
- names, referencing
- reserved properties
- project files, referencing
ms.assetid: c8fcc594-5d37-4e2e-b070-4d9c012043b5
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 29960de09b512a419a56a61f493702485c287475
ms.sourcegitcommit: 4ae5e9817ad13edd05425febb322b5be6d3c3425
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/11/2020
ms.locfileid: "90036460"
---
# <a name="how-to-reference-the-name-or-location-of-the-project-file"></a>Instrukcje: odwoływanie się do nazwy lub lokalizacji pliku projektu

Możesz użyć nazwy lub lokalizacji projektu w samym pliku projektu bez konieczności tworzenia własnej właściwości. MSBuild zawiera zastrzeżone właściwości, które odwołują się do nazwy pliku projektu i innych właściwości związanych z projektem. Aby uzyskać więcej informacji na temat właściwości zastrzeżonych, zobacz [Właściwości zarezerwowane i dobrze znane programu MSBuild](../msbuild/msbuild-reserved-and-well-known-properties.md).

## <a name="use-the-project-properties"></a>Korzystanie z właściwości projektu

 MSBuild zawiera pewne zastrzeżone właściwości, których można użyć w plikach projektu bez definiowania ich za każdym razem. Na przykład Właściwość zastrzeżone `MSBuildProjectName` zawiera odwołanie do nazwy pliku projektu. Właściwość zastrzeżona `MSBuildProjectDirectory` zawiera odwołanie do lokalizacji pliku projektu.

#### <a name="to-use-the-project-properties"></a>Aby użyć właściwości projektu

- Odwoływanie się do właściwości w pliku projektu za pomocą notacji $ (), tak jak w przypadku każdej właściwości. Na przykład:

  ```xml
  <CSC Sources = "@(CSFile)"
      OutputAssembly = "$(MSBuildProjectName).exe"/>
  </CSC>
  ```

  Zaletą użycia zastrzeżonej właściwości jest to, że wszelkie zmiany nazwy pliku projektu są włączane automatycznie. Przy następnym kompilowaniu projektu plik wyjściowy będzie miał nową nazwę, która nie wymaga żadnych dalszych akcji.

  Aby uzyskać więcej informacji na temat używania znaków specjalnych w odwołaniach do pliku lub projektu, zobacz [znaki specjalne MSBuild](../msbuild/msbuild-special-characters.md).

> [!NOTE]
> W pliku projektu nie można ponownie zdefiniować zarezerwowanych właściwości.

## <a name="example"></a>Przykład

 Następujący przykładowy plik projektu odwołuje się do nazwy projektu jako zastrzeżonej właściwości, aby określić nazwę danych wyjściowych.

```xml
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003"
    DefaultTargets = "Compile">

    <!-- Specify the inputs -->
    <ItemGroup>
        <CSFile Include = "consolehwcs1.cs"/>
     </ItemGroup>
    <Target Name = "Compile">
        <!-- Run the Visual C# compilation using
        input files of type CSFile -->
        <CSC Sources = "@(CSFile)"
            OutputAssembly = "$(MSBuildProjectName).exe" >
            <!-- Set the OutputAssembly attribute of the CSC task
            to the name of the project -->
            <Output
                TaskParameter = "OutputAssembly"
                ItemName = "EXEFile" />
        </CSC>
        <!-- Log the file name of the output file -->
        <Message Text="The output file is @(EXEFile)"/>
    </Target>
</Project>
```

## <a name="example"></a>Przykład

 Poniższy przykładowy plik projektu używa `MSBuildProjectDirectory` Właściwości zastrzeżonej do utworzenia pełnej ścieżki do pliku w lokalizacji pliku projektu.

```xml
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">

    <!-- Build the path to a file in the root of the project -->
    <PropertyGroup>
        <NewFilePath>$([System.IO.Path]::Combine($(MSBuildProjectDirectory), `BuildInfo.txt`))</NewFilePath>
    </PropertyGroup>
</Project>
```

W przykładzie użyto składni [funkcji właściwości](property-functions.md) do wywołania metody statycznej .NET Framework <xref:System.IO.Path.Combine*?displayProperty=fullName> .

## <a name="see-also"></a>Zobacz także

- [MSBuild](../msbuild/msbuild.md)
- [Zarezerwowane i dobrze znane właściwości programu MSBuild](../msbuild/msbuild-reserved-and-well-known-properties.md)
