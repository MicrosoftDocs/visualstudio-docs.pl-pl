---
title: 'Jak: Odwoływać się do nazwy lub lokalizacji pliku projektu | Dokumenty firmy Microsoft'
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
ms.openlocfilehash: 2b54a63b135f844ff20b45ffac430662c4df1f19
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "77633840"
---
# <a name="how-to-reference-the-name-or-location-of-the-project-file"></a>Jak: Odwoływanie się do nazwy lub lokalizacji pliku projektu

Można użyć nazwy lub lokalizacji projektu w samym pliku projektu bez konieczności tworzenia własnej właściwości. MSBuild udostępnia właściwości zastrzeżone, które odwołują się do nazwy pliku projektu i innych właściwości związanych z projektem. Aby uzyskać więcej informacji na temat właściwości zarezerwowanych, zobacz [MSBuild zastrzeżone i dobrze znane właściwości](../msbuild/msbuild-reserved-and-well-known-properties.md).

## <a name="use-the-project-properties"></a>Korzystanie z właściwości projektu

 MSBuild udostępnia niektóre zastrzeżone właściwości, których można używać w plikach projektu bez definiowania ich za każdym razem. Na przykład właściwość `MSBuildProjectName` reserved zawiera odwołanie do nazwy pliku projektu. Właściwość `MSBuildProjectDirectory` reserved zawiera odwołanie do lokalizacji pliku projektu.

#### <a name="to-use-the-project-properties"></a>Aby użyć właściwości projektu

- Odwołaj się do właściwości w pliku projektu z notacją $(), tak jak w przypadku dowolnej właściwości. Przykład:

  ```xml
  <CSC Sources = "@(CSFile)"
      OutputAssembly = "$(MSBuildProjectName).exe"/>
  </CSC>
  ```

  Zaletą korzystania z właściwości zastrzeżone jest to, że wszelkie zmiany w nazwie pliku projektu są włączane automatycznie. Przy następnym utworzeniu projektu plik wyjściowy będzie miał nową nazwę bez dalszych działań wymaganych z Twojej strony.

  Aby uzyskać więcej informacji na temat używania znaków specjalnych w odwołaniach do plików lub projektów, zobacz [ZNAKI SPECJALNE MSBuild](../msbuild/msbuild-special-characters.md).

> [!NOTE]
> Właściwości zarezerwowane nie można ponownie zdefiniować w pliku projektu.

## <a name="example"></a>Przykład

 Poniższy przykładowy plik projektu odwołuje się do nazwy projektu jako właściwości zarezerwowanej, aby określić nazwę danych wyjściowych.

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

 Poniższy przykładowy plik `MSBuildProjectDirectory` projektu używa właściwości zarezerwowanej do utworzenia pełnej ścieżki do pliku w lokalizacji pliku projektu.

```xml
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">

    <!-- Build the path to a file in the root of the project -->
    <PropertyGroup>
        <NewFilePath>$([System.IO.Path]::Combine($(MSBuildProjectDirectory), `BuildInfo.txt`))</NewFilePath>
    </PropertyGroup>
</Project>
```

W przykładzie użyto składni [funkcji Właściwość,](property-functions.md) aby <xref:System.IO.Path.Combine*?displayProperty=fullName>wywołać statyczną metodę .NET Framework .

## <a name="see-also"></a>Zobacz też

- [Msbuild](../msbuild/msbuild.md)
- [MSBuild zastrzeżone i dobrze znane właściwości](../msbuild/msbuild-reserved-and-well-known-properties.md)
