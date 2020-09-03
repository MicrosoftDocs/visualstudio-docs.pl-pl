---
title: 'Instrukcje: wykluczanie plików z kompilacji | Microsoft Docs'
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "77633866"
---
# <a name="how-to-exclude-files-from-the-build"></a>Instrukcje: wykluczanie plików z kompilacji

W pliku projektu można użyć symboli wieloznacznych, aby uwzględnić wszystkie pliki w jednym katalogu lub zagnieżdżony zestaw katalogów jako dane wejściowe dla kompilacji. Jednak może istnieć jeden plik w katalogu lub jeden katalog w zagnieżdżonym zestawie katalogów, które nie mają być uwzględniane jako dane wejściowe dla kompilacji. Można jawnie wykluczyć ten plik lub katalog z listy danych wejściowych. Może to być również plik w projekcie, który ma być uwzględniony tylko w określonych warunkach. Można jawnie zadeklarować warunki, w których plik jest uwzględniony w kompilacji.

## <a name="exclude-a-file-or-directory-from-the-inputs-for-a-build"></a>Wyklucz plik lub katalog z danych wejściowych dla kompilacji

 Listy elementów są plikami wejściowymi dla kompilacji. Elementy, które mają zostać uwzględnione, są deklarowane osobno lub jako Grupa przy użyciu `Include` atrybutu. Na przykład:

```xml
<CSFile Include="Form1.cs"/>
<CSFile Include ="File1.cs;File2.cs"/>
<CSFile Include="*.cs"/>
<JPGFile Include="Images\**\*.jpg"/>
```

 Jeśli użyto symboli wieloznacznych, aby uwzględnić wszystkie pliki w jednym katalogu lub zagnieżdżony zestaw katalogów jako dane wejściowe dla kompilacji, może istnieć co najmniej jeden plik w katalogu lub jeden katalog w zagnieżdżonym zestawie katalogów, które nie mają być uwzględniane. Aby wykluczyć element z listy elementów, użyj `Exclude` atrybutu.

#### <a name="to-include-all-cs-or-vb-files-except-form2"></a>Uwzględnienie wszystkich plików *CS* lub *VB* z wyjątkiem *Form2*

- Użyj jednego z następujących `Include` `Exclude` atrybutów:

    ```xml
    <CSFile Include="*.cs" Exclude="Form2.cs"/>
    ```

    lub

    ```xml
    <VBFile Include="*.vb" Exclude="Form2.vb"/>
    ```

#### <a name="to-include-all-cs-or-vb-files-except-form2-and-form3"></a>Uwzględnienie wszystkich plików *CS* lub *VB* z wyjątkiem *Form2* i *Form3*

- Użyj jednego z następujących `Include` `Exclude` atrybutów:

    ```xml
    <CSFile Include="*.cs" Exclude="Form2.cs;Form3.cs"/>
    ```

    lub

    ```xml
    <VBFile Include="*.vb" Exclude="Form2.vb;Form3.vb"/>
    ```

#### <a name="to-include-all-jpg-files-in-subdirectories-of-the-images-directory-except-those-in-the-version2-directory"></a>W celu uwzględnienia wszystkich plików *jpg* w podkatalogach katalogu *obrazów* , z wyjątkiem tych znajdujących się w katalogu *Version2*

- Użyj następujących `Include` atrybutów i `Exclude` :

    ```xml
    <JPGFile
        Include="Images\**\*.jpg"
        Exclude = "Images\**\Version2\*.jpg"/>
    ```

    > [!NOTE]
    > Należy określić ścieżkę dla obu atrybutów. Jeśli ścieżka bezwzględna jest używana do określania lokalizacji plików w `Include` atrybucie, należy również użyć ścieżki absolutnej w atrybucie `Exclude` . Jeśli używasz ścieżki względnej w `Include` atrybucie, należy również użyć ścieżki względnej w `Exclude` atrybucie.

## <a name="use-conditions-to-exclude-a-file-or-directory-from-the-inputs-for-a-build"></a>Użyj warunków, aby wykluczyć plik lub katalog z danych wejściowych dla kompilacji

 Jeśli istnieją elementy, które mają zostać uwzględnione, na przykład w kompilacji debugowania, ale nie na kompilacji, można użyć `Condition` atrybutu, aby określić warunki, w których ma zostać uwzględniony element.

#### <a name="to-include-the-file-formulavb-only-in-release-builds"></a>Aby dołączyć plik *Formula. vb* tylko w kompilacjach wydania

- Użyj `Condition` atrybutu podobnego do poniższego:

    ```xml
    <Compile
        Include="Formula.vb"
        Condition=" '$(Configuration)' == 'Release' " />
    ```

## <a name="example"></a>Przykład

 Poniższy przykład kodu kompiluje projekt ze wszystkimi plikami *CS* w katalogu, z wyjątkiem *Form2.cs*.

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

- [Elementy](../msbuild/msbuild-items.md)
- [MSBuild](../msbuild/msbuild.md)
- [Instrukcje: Wybieranie plików do skompilowania](../msbuild/how-to-select-the-files-to-build.md)
