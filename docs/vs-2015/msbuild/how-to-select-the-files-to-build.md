---
title: 'Instrukcje: Wybieranie plików do kompilacji | Dokumentacja firmy Microsoft'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
ms.topic: conceptual
helpviewer_keywords:
- MSBuild, wildcards
- MSBuild, including files
- Include attribute [MSBuild]
ms.assetid: f5ff182f-7b3a-46fb-9335-37df54cfb8eb
caps.latest.revision: 17
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 0968dd8914b99e8d47ef1364231059175aaf73fe
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "63437907"
---
# <a name="how-to-select-the-files-to-build"></a>Instrukcje: Wybieranie plików do kompilacji
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Podczas kompilowania projektu, zawiera kilka plików, możesz wyświetlić listę każdego pliku osobno w pliku projektu lub można używać symboli wieloznacznych, aby uwzględnić wszystkie pliki w jednym katalogu lub zagnieżdżone zestawu katalogów.  
  
## <a name="specifying-inputs"></a>Określanie danych wejściowych  
 Elementy reprezentują dane wejściowe dla kompilacji. Aby uzyskać więcej informacji na temat elementów, zobacz [elementów](../msbuild/msbuild-items.md).  
  
 Aby uwzględnić pliki dla kompilacji, muszą być uwzględnione na liście elementów w [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] pliku projektu. Wiele plików można dodać do listy elementów przy tym pliki pojedynczo lub przy użyciu symboli wieloznacznych, aby uwzględnić wiele plików jednocześnie.  
  
#### <a name="to-declare-items-individually"></a>Aby zadeklarować elementy pojedynczo  
  
- Użyj `Include` atrybuty podobne do następujących:  
  
     `<CSFile Include="form1.cs"/>`  
  
     — lub —  
  
     `<VBFile Include="form1.vb"/>`  
  
    > [!NOTE]
    > Jeśli elementy w kolekcji elementów nie znajdują się w tym samym katalogu co plik projektu, należy określić pełną lub względną ścieżkę do elementu. Na przykład: `Include="..\..\form2.cs"`.  
  
#### <a name="to-declare-multiple-items"></a>Aby zadeklarować wiele elementów  
  
- Użyj `Include` atrybuty podobne do następujących:  
  
     `<CSFile Include="form1.cs;form2.cs"/>`  
  
     — lub —  
  
     `<VBFile Include="form1.vb;form2.vb"/>`  
  
## <a name="specifying-inputs-with-wildcards"></a>Określanie danych wejściowych z symbolami wieloznacznymi  
 Można również użyć symboli wieloznacznych rekursywnie obejmują wszystkie pliki lub tylko określone pliki z podkatalogi jako dane wejściowe dla kompilacji. Aby uzyskać więcej informacji na temat symboli wieloznacznych, zobacz [elementów](../msbuild/msbuild-items.md)  
  
 Poniższe przykłady są oparte na projekt, który zawiera pliki graficzne w następujące katalogi i podkatalogi, przy użyciu pliku projektu, znajdujący się w katalogu projektu:  
  
 Project\Images\BestJpgs  
  
 Project\Images\ImgJpgs  
  
 Project\Images\ImgJpgs\Img1  
  
#### <a name="to-include-all-jpg-files-in-the-images-directory-and-subdirectories"></a>Aby objąć wszystkie pliki jpg obrazów katalogu i podkatalogach  
  
- Należy użyć następującego `Include` atrybutu:  
  
     `Include="Images\**\*.jpg"`  
  
#### <a name="to-include-all-jpg-files-starting-with-img"></a>Aby włączyć wszystkie pliki jpg, rozpoczynając od "img"  
  
- Należy użyć następującego `Include` atrybutu:  
  
     `Include="Images\**\img*.jpg"`  
  
#### <a name="to-include-all-files-in-directories-with-names-ending-in-jpgs"></a>Aby włączyć wszystkie pliki w katalogach przy użyciu nazwy kończące się na "jpg"  
  
- Użyj jednej z następujących `Include` atrybuty:  
  
     `Include="Images\**\*jpgs\*.*"`  
  
     — lub —  
  
     `Include="Images\**\*jpgs\*"`  
  
## <a name="passing-items-to-a-task"></a>Przekazywanie elementów do zadania  
 W pliku projektu, można użyć @ notacji () w zadaniach, aby określić listę całego elementu jako dane wejściowe dla kompilacji. Możesz użyć tej notacji, wyświetlić listę wszystkich plików osobno lub używać symboli wieloznacznych.  
  
#### <a name="to-use-all-visual-c-or-visual-basic-files-as-inputs"></a>Aby używać wszystkich Visual C# lub Visual Basic plików jako dane wejściowe  
  
- Użyj `Include` atrybuty podobny do następującego:  
  
     `<CSC Sources="@(CSFile)">...</CSC>`  
  
     — lub —  
  
     `<VBC Sources="@(VBFile)">...</VBC>`  
  
> [!NOTE]
> Należy użyć symboli wieloznacznych przy użyciu elementów do określ dane wejściowe dla kompilacji; Nie można określić przy użyciu danych wejściowych `Sources` atrybutu w [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] zadań, takich jak [Csc](../msbuild/csc-task.md) lub [Vbc](../msbuild/vbc-task.md). Poniższy przykład jest nieprawidłowy w pliku projektu:  
>   
> `<CSC Sources="*.cs">...</CSC>`  
  
## <a name="example"></a>Przykład  
 Poniższy przykład kodu pokazuje projekt, który zawiera wszystkie pliki wejściowe oddzielnie.  
  
```  
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
 Poniższy przykład kodu używa symbol wieloznaczny, obejmujący wszystkie pliki CS.  
  
```  
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
 [Instrukcje: Wykluczanie plików z kompilacji](../msbuild/how-to-exclude-files-from-the-build.md)   
 [Elementy](../msbuild/msbuild-items.md)
