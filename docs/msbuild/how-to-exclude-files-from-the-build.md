---
title: 'Jak: Wykluczanie plików z kompilacji | Dokumenty firmy Microsoft'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- MSBuild, wildcards
- MSBuild, excluding files
- wildcards, MSBuild
ms.assetid: 1be36e45-01da-451c-972d-f9fc0e7d663c
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 1914f709a69dbb120e4439ddceeda8b70ad570b4
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "77633866"
---
# <a name="how-to-exclude-files-from-the-build"></a>Jak: Wykluczanie plików z kompilacji

W pliku projektu można użyć symboli wieloznacznych, aby uwzględnić wszystkie pliki w jednym katalogu lub zagnieżdżony zestaw katalogów jako dane wejściowe dla kompilacji. Jednak może istnieć jeden plik w katalogu lub jeden katalog w zagnieżdżonej zestaw katalogów, które nie mają być uwzględnione jako dane wejściowe dla kompilacji. Można jawnie wykluczyć ten plik lub katalog z listy danych wejściowych. Może również istnieć plik w projekcie, który chcesz dołączyć tylko pod pewnymi warunkami. Można jawnie zadeklarować warunki, w których plik jest zawarty w kompilacji.

## <a name="exclude-a-file-or-directory-from-the-inputs-for-a-build"></a>Wykluczanie pliku lub katalogu z danych wejściowych kompilacji

 Listy elementów są plikami wejściowymi kompilacji. Elementy, które mają zostać uwzględnione są zadeklarowane oddzielnie `Include` lub jako grupa przy użyciu atrybutu. Przykład:

```xml
<CSFile Include="Form1.cs"/>
<CSFile Include ="File1.cs;File2.cs"/>
<CSFile Include="*.cs"/>
<JPGFile Include="Images\**\*.jpg"/>
```

 Jeśli użyto symboli wieloznacznych do uwzględnienia wszystkich plików w jednym katalogu lub zagnieżdżonego zestawu katalogów jako danych wejściowych dla kompilacji, może istnieć jeden lub więcej plików w katalogu lub jeden katalog w zagnieżdżonej zestawie katalogów, których nie chcesz dołączać. Aby wykluczyć element z listy elementów, użyj tego atrybutu. `Exclude`

#### <a name="to-include-all-cs-or-vb-files-except-form2"></a>Aby uwzględnić wszystkie pliki *cs* lub *.vb* z wyjątkiem *formularza 2*

- Użyj jednego z `Include` `Exclude` następujących atrybutów:

    ```xml
    <CSFile Include="*.cs" Exclude="Form2.cs"/>
    ```

    lub

    ```xml
    <VBFile Include="*.vb" Exclude="Form2.vb"/>
    ```

#### <a name="to-include-all-cs-or-vb-files-except-form2-and-form3"></a>Aby uwzględnić wszystkie pliki *cs* lub *.vb* z wyjątkiem *form 2* i *form3*

- Użyj jednego z `Include` `Exclude` następujących atrybutów:

    ```xml
    <CSFile Include="*.cs" Exclude="Form2.cs;Form3.cs"/>
    ```

    lub

    ```xml
    <VBFile Include="*.vb" Exclude="Form2.vb;Form3.vb"/>
    ```

#### <a name="to-include-all-jpg-files-in-subdirectories-of-the-images-directory-except-those-in-the-version2-directory"></a>Aby uwzględnić wszystkie pliki *jpg* w podkatalogach katalogu *Obrazy,* z wyjątkiem tych w katalogu *Version2*

- Użyj następujących `Include` `Exclude` atrybutów:

    ```xml
    <JPGFile
        Include="Images\**\*.jpg"
        Exclude = "Images\**\Version2\*.jpg"/>
    ```

    > [!NOTE]
    > Należy określić ścieżkę dla obu atrybutów. Jeśli używasz ścieżki bezwzględnej do `Include` określania lokalizacji plików w atrybucie, należy również użyć ścieżki bezwzględnej w atrybucie; `Exclude` Jeśli używasz ścieżki względnej w `Include` atrybucie, należy `Exclude` również użyć ścieżki względnej w atrybucie.

## <a name="use-conditions-to-exclude-a-file-or-directory-from-the-inputs-for-a-build"></a>Użyj warunków, aby wykluczyć plik lub katalog z danych wejściowych kompilacji

 Jeśli istnieją elementy, które mają zostać uwzględnione, na przykład w kompilacji debugowania, ale nie release kompilacji, można użyć atrybutu, `Condition` aby określić warunki, w których mają być dołączane element.

#### <a name="to-include-the-file-formulavb-only-in-release-builds"></a>Aby dołączyć plik *Formula.vb* tylko w kompilacjach wersji

- Użyj `Condition` atrybutu podobnego do następującego:

    ```xml
    <Compile
        Include="Formula.vb"
        Condition=" '$(Configuration)' == 'Release' " />
    ```

## <a name="example"></a>Przykład

 Poniższy przykład kodu tworzy projekt ze wszystkimi plikami *cs* w katalogu z wyjątkiem *Form2.cs*.

```xml
<Project DefaultTargets="Compile"
    xmlns="http://schemas.microsoft.com/developer/msbuild/2003" >

    <PropertyGroup>
        <builtdir>built</builtdir>
    </PropertyGroup>

    <ItemGroup>
        <CSFile Include="*.cs" Exclude="Form2.cs"/>

        <Reference Include="System.dll"/>
        <Reference Include="System.Data.dll"/>
        <Reference Include="System.Drawing.dll"/>
        <Reference Include="System.Windows.Forms.dll"/>
        <Reference Include="System.XML.dll"/>
    </ItemGroup>

    <Target Name="PreBuild">
        <Exec Command="if not exist $(builtdir) md $(builtdir)"/>
    </Target>

    <Target Name="Compile" DependsOnTargets="PreBuild">
        <Csc Sources="@(CSFile)"
            References="@(Reference)"
            OutputAssembly="$(builtdir)\$(MSBuildProjectName).exe"
            TargetType="exe" />
    </Target>
</Project>
```

## <a name="see-also"></a>Zobacz też

- [Items](../msbuild/msbuild-items.md)
- [Msbuild](../msbuild/msbuild.md)
- [Jak: Wybierz pliki do utworzenia](../msbuild/how-to-select-the-files-to-build.md)
