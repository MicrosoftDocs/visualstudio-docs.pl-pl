---
title: 'Jak: Wybierz pliki do zbudowania | Dokumenty firmy Microsoft'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- MSBuild, wildcards
- MSBuild, including files
- Include attribute [MSBuild]
ms.assetid: f5ff182f-7b3a-46fb-9335-37df54cfb8eb
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 0566078c7f90faf204c35024e2c308b5ef881c01
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "77633814"
---
# <a name="how-to-select-the-files-to-build"></a>Jak: Wybierz pliki do utworzenia

Podczas tworzenia projektu zawierającego kilka plików można wyświetlić osobno każdy plik w pliku projektu lub użyć symboli wieloznacznych, aby uwzględnić wszystkie pliki w jednym katalogu lub zagnieżdżony zestaw katalogów.

## <a name="specify-inputs"></a>Określanie danych wejściowych

Elementy reprezentują dane wejściowe dla kompilacji. Aby uzyskać więcej informacji na temat elementów, zobacz [Elementy](../msbuild/msbuild-items.md).

Aby dołączyć pliki kompilacji, muszą one zostać uwzględnione na liście elementów w pliku projektu MSBuild. Wiele plików można dodać do list elementów, dołączając pliki indywidualnie lub używając symboli wieloznacznych, aby dołączyć wiele plików jednocześnie.

#### <a name="to-declare-items-individually"></a>Aby zadeklarować elementy indywidualnie

- Użyj `Include` atrybutów podobnych do następujących:

    `<CSFile Include="form1.cs"/>`

    lub

    `<VBFile Include="form1.vb"/>`

    > [!NOTE]
    > Jeśli elementy w kolekcji elementów nie znajdują się w tym samym katalogu co plik projektu, należy określić pełną lub względną ścieżkę do elementu. Na przykład: `Include="..\..\form2.cs"`.

#### <a name="to-declare-multiple-items"></a>Aby zadeklarować wiele elementów

- Użyj `Include` atrybutów podobnych do następujących:

    `<CSFile Include="form1.cs;form2.cs"/>`

    lub

    `<VBFile Include="form1.vb;form2.vb"/>`

## <a name="specify-inputs-with-wildcards"></a>Określanie danych wejściowych z symbolami wieloznaczowymi

Można również użyć symboli wieloznacznych, aby rekursywnie dołączyć wszystkie pliki lub tylko określone pliki z podkatalogów jako dane wejściowe dla kompilacji. Aby uzyskać więcej informacji na temat symboli wieloznacznych, zobacz [Elementy](../msbuild/msbuild-items.md)

Poniższe przykłady są oparte na projekcie, który zawiera pliki graficzne w następujących katalogach i podkatalogach, z plikiem projektu znajdującym się w katalogu *projektu:*

*Projekt\Obrazy\Najlepsze dżpgi*

*Projekt\Obrazy\ImgJpgs*

*Projekt\Obrazy\ImgJpgs\Img1*

#### <a name="to-include-all-jpg-files-in-the-images-directory-and-subdirectories"></a>Aby uwzględnić wszystkie pliki *jpg* w katalogu *Obrazy* i podkatalogach

- Użyj następującego `Include` atrybutu:

    `Include="Images\**\*.jpg"`

#### <a name="to-include-all-jpg-files-starting-with-img"></a>Aby uwzględnić wszystkie pliki *jpg,* począwszy od *img*

- Użyj następującego `Include` atrybutu:

    `Include="Images\**\img*.jpg"`

#### <a name="to-include-all-files-in-directories-with-names-ending-in-jpgs"></a>Aby uwzględnić wszystkie pliki w katalogach o nazwach kończących się na *rozszerkach*

- Użyj jednego z `Include` następujących atrybutów:

    `Include="Images\**\*jpgs\*.*"`

    lub

    `Include="Images\**\*jpgs\*"`

## <a name="pass-items-to-a-task"></a>Przekazywanie elementów do zadania

W pliku projektu można użyć notacji @() w zadaniach, aby określić całą listę elementów jako dane wejściowe dla kompilacji. Można użyć tej notacji, czy lista wszystkich plików oddzielnie lub użyć symboli wieloznacznych.

#### <a name="to-use-all-visual-c-or-visual-basic-files-as-inputs"></a>Aby używać wszystkich plików visual c# lub Visual Basic jako danych wejściowych

- Użyj `Include` atrybutów podobnych do następujących:

    `<CSC Sources="@(CSFile)">...</CSC>`

    lub

    `<VBC Sources="@(VBFile)">...</VBC>`

> [!NOTE]
> Należy użyć symboli wieloznacznych z elementami, aby określić dane wejściowe dla kompilacji; nie można określić danych `Sources` wejściowych przy użyciu atrybutu w zadaniach MSBuild, takich jak [Csc](../msbuild/csc-task.md) lub [Vbc](../msbuild/vbc-task.md). Poniższy przykład jest nieprawidłowy w pliku projektu:
>
> `<CSC Sources="*.cs">...</CSC>`

## <a name="example"></a>Przykład

Poniższy przykład kodu pokazuje projekt, który zawiera wszystkie pliki wejściowe oddzielnie.

```xml
<Project DefaultTargets="Compile"
    xmlns="http://schemas.microsoft.com/developer/msbuild/2003" >
    <PropertyGroup>
        <Builtdir>built</Builtdir>
    </PropertyGroup>

    <ItemGroup>
        <CSFile Include="Form1.cs"/>
        <CSFile Include="AssemblyInfo.cs"/>

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

## <a name="example"></a>Przykład

Poniższy przykład kodu używa symbolu wieloznacznego, aby uwzględnić wszystkie pliki *cs.*

```xml
<Project DefaultTargets="Compile"
    xmlns="http://schemas.microsoft.com/developer/msbuild/2003" >

    <PropertyGroup>
        <builtdir>built</builtdir>
    </PropertyGroup>

    <ItemGroup>
        <CSFile Include="*.cs"/>

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

- [Jak: Wykluczanie plików z kompilacji](../msbuild/how-to-exclude-files-from-the-build.md)
- [Items](../msbuild/msbuild-items.md)
