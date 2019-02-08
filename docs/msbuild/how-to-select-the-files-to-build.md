---
title: 'Instrukcje: Wybieranie plików do kompilacji | Dokumentacja firmy Microsoft'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- MSBuild, wildcards
- MSBuild, including files
- Include attribute [MSBuild]
ms.assetid: f5ff182f-7b3a-46fb-9335-37df54cfb8eb
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 54cd1e9855bbc09a0045cd50ac26c1aef38bac2c
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2019
ms.locfileid: "55942816"
---
# <a name="how-to-select-the-files-to-build"></a>Instrukcje: Wybieranie plików do kompilacji
Podczas kompilowania projektu, zawiera kilka plików, możesz wyświetlić listę każdego pliku osobno w pliku projektu lub można używać symboli wieloznacznych, aby uwzględnić wszystkie pliki w jednym katalogu lub zagnieżdżone zestawu katalogów.

## <a name="specify-inputs"></a>Określ dane wejściowe
Elementy reprezentują dane wejściowe dla kompilacji. Aby uzyskać więcej informacji na temat elementów, zobacz [elementów](../msbuild/msbuild-items.md).

Aby uwzględnić pliki dla kompilacji, muszą być uwzględnione na liście elementów w [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] pliku projektu. Wiele plików można dodać do listy elementów przy tym pliki pojedynczo lub przy użyciu symboli wieloznacznych, aby uwzględnić wiele plików jednocześnie.

#### <a name="to-declare-items-individually"></a>Aby zadeklarować elementy pojedynczo

- Użyj `Include` atrybuty podobne do następujących:  
  
    `<CSFile Include="form1.cs"/>`  
  
    lub  
  
    `<VBFile Include="form1.vb"/>`  
  
    > [!NOTE]
    > Jeśli elementy w kolekcji elementów nie znajdują się w tym samym katalogu co plik projektu, należy określić pełną lub względną ścieżkę do elementu. Na przykład: `Include="..\..\form2.cs"`.

#### <a name="to-declare-multiple-items"></a>Aby zadeklarować wiele elementów

-   Użyj `Include` atrybuty podobne do następujących:  
  
    `<CSFile Include="form1.cs;form2.cs"/>`  
  
    lub  
  
    `<VBFile Include="form1.vb;form2.vb"/>`

## <a name="specify-inputs-with-wildcards"></a>Określ dane wejściowe z symbolami wieloznacznymi
Można również użyć symboli wieloznacznych rekursywnie obejmują wszystkie pliki lub tylko określone pliki z podkatalogi jako dane wejściowe dla kompilacji. Aby uzyskać więcej informacji na temat symboli wieloznacznych, zobacz [elementów](../msbuild/msbuild-items.md)

Poniższe przykłady są oparte na projekt, który zawiera pliki grafiki w następujących katalogów i podkatalogów, przy użyciu pliku projektu na terenie *projektu* katalogu:

*Project\Images\BestJpgs*

*Project\Images\ImgJpgs*

*Project\Images\ImgJpgs\Img1*

#### <a name="to-include-all-jpg-files-in-the-images-directory-and-subdirectories"></a>Aby uwzględnić wszystkie *.jpg* pliki *obrazów* katalogu i podkatalogach

- Należy użyć następującego `Include` atrybutu:  
  
    `Include="Images\**\*.jpg"`

#### <a name="to-include-all-jpg-files-starting-with-img"></a>Aby uwzględnić wszystkie *.jpg* pliki *img*

- Należy użyć następującego `Include` atrybutu:  
  
    `Include="Images\**\img*.jpg"`

#### <a name="to-include-all-files-in-directories-with-names-ending-in-jpgs"></a>Aby włączyć wszystkie pliki w katalogach przy użyciu nazwy kończące się na *jpg*

- Użyj jednej z następujących `Include` atrybuty:  
  
    `Include="Images\**\*jpgs\*.*"`  
  
    lub  
  
    `Include="Images\**\*jpgs\*"`

## <a name="pass-items-to-a-task"></a>Przekazywanie elementów do zadania
W pliku projektu, można użyć @ notacji () w zadaniach, aby określić listę całego elementu jako dane wejściowe dla kompilacji. Możesz użyć tej notacji, wyświetlić listę wszystkich plików osobno lub używać symboli wieloznacznych.

#### <a name="to-use-all-visual-c-or-visual-basic-files-as-inputs"></a>Aby używać wszystkich Visual C# lub Visual Basic plików jako dane wejściowe

- Użyj `Include` atrybuty podobny do następującego:  
  
    `<CSC Sources="@(CSFile)">...</CSC>`  
  
    lub  
  
    `<VBC Sources="@(VBFile)">...</VBC>`

> [!NOTE]
>  Przy użyciu elementów należy użyć symboli wieloznacznych, aby określić dane wejściowe dla kompilacji; Nie można określić przy użyciu danych wejściowych `Sources` atrybutu w [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] zadań, takich jak [Csc](../msbuild/csc-task.md) lub [Vbc](../msbuild/vbc-task.md). Poniższy przykład jest nieprawidłowy w pliku projektu:
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
Poniższy przykład kodu wykorzystuje symboli wieloznacznych, aby uwzględnić wszystkie *.cs* plików.

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

## <a name="see-also"></a>Zobacz także
[Instrukcje: Wykluczanie plików z kompilacji](../msbuild/how-to-exclude-files-from-the-build.md)  
[Elementy](../msbuild/msbuild-items.md)
