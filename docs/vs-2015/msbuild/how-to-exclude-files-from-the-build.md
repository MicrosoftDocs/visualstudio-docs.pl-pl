---
title: 'Instrukcje: Wykluczanie plików z kompilacji | Dokumentacja firmy Microsoft'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
ms.topic: conceptual
helpviewer_keywords:
- MSBuild, wildcards
- MSBuild, excluding files
- wildcards, MSBuild
ms.assetid: 1be36e45-01da-451c-972d-f9fc0e7d663c
caps.latest.revision: 19
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: bd1535841a01b6e188383d74ed3b6124b4a325f6
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2019
ms.locfileid: "60052562"
---
# <a name="how-to-exclude-files-from-the-build"></a>Instrukcje: Wykluczanie plików z kompilacji
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

W pliku projektu można używać symboli wieloznacznych, aby uwzględnić wszystkie pliki w jednym katalogu lub zagnieżdżone zestawu katalogów jako dane wejściowe dla kompilacji. Jednak może być jeden plik w katalogu lub w katalogu w zestawie zagnieżdżonych katalogów, których nie chcesz dodać jako dane wejściowe dla kompilacji. Można jawnie wykluczone tego pliku lub katalogu, z listy danych wejściowych. W projekcie, który chcesz uwzględnić w pewnych okolicznościach również może być plikiem. Można jawnie zadeklarować warunków, w których plik jest uwzględniony w kompilacji.  
  
## <a name="excluding-a-file-or-directory-from-the-inputs-for-a-build"></a>Wykluczanie pliku lub katalogu dane wejściowe dla kompilacji  
 Element listy są pliki wejściowe dla kompilacji. Elementy, które mają zostać uwzględnione są deklarowane, oddzielnie lub jako grupę za pomocą `Include` atrybutu. Na przykład:  
  
```  
<CSFile Include="Form1.cs"/>  
<CSFile Include ="File1.cs;File2.cs"/>  
<CSFile Include="*.cs"/>  
<JPGFile Include="Images\**\*.jpg"/>  
```  
  
 Jeśli używano symboli wieloznacznych, aby uwzględnić wszystkie pliki w jednym katalogu lub zagnieżdżone zestawu katalogów jako dane wejściowe dla kompilacji, może być jeden lub więcej plików w katalogu lub jednego katalogu w zagnieżdżonych zestawu katalogów, których nie chcesz dołączyć. Aby wyłączyć element z listy elementów, należy użyć `Exclude` atrybutu.  
  
#### <a name="to-include-all-cs-or-vb-files-except-form2"></a>Aby włączyć wszystkie pliki CS lub .vb, z wyjątkiem formularz2  
  
- Użyj jednej z następujących `Include` i `Exclude` atrybuty:  
  
    ```  
    <CSFile Include="*.cs" Exclude="Form2.cs"/>  
    ```  
  
     - lub —  
  
    ```  
    <VBFile Include="*.vb" Exclude="Form2.vb"/>  
    ```  
  
#### <a name="to-include-all-cs-or-vb-files-except-form2-and-form3"></a>Aby włączyć wszystkie pliki CS lub .vb, z wyjątkiem Formularz2 i Form3  
  
- Użyj jednej z następujących `Include` i `Exclude` atrybuty:  
  
    ```  
    <CSFile Include="*.cs" Exclude="Form2.cs;Form3.cs"/>  
    ```  
  
     - lub —  
  
    ```  
    <VBFile Include="*.vb" Exclude="Form2.vb;Form3.vb"/>  
    ```  
  
#### <a name="to-include-all-jpg-files-in-subdirectories-of-the-images-directory-except-those-in-the-version2-directory"></a>Aby włączyć wszystkie pliki jpg podkatalogi katalogu obrazów, z wyjątkiem tych, które w katalogu Version2  
  
- Należy użyć następującego `Include` i `Exclude` atrybuty:  
  
    ```  
    <JPGFile  
        Include="Images\**\*.jpg"  
        Exclude = "Images\**\Version2\*.jpg"/>  
    ```  
  
    > [!NOTE]
    >  Należy określić ścieżkę dla obu atrybutów. Jeśli używasz ścieżki bezwzględnej do określenia lokalizacji plików w `Include` atrybutu, należy również użyć ścieżką bezwzględną `Exclude` atrybutu; Jeśli używasz ścieżki względnej `Include` atrybutu, należy również użyć ścieżki względnej w `Exclude`atrybutu.  
  
## <a name="using-conditions-to-exclude-a-file-or-directory-from-the-inputs-for-a-build"></a>Za pomocą warunków do wykluczenia pliku lub katalogu z danych wejściowych dla kompilacji  
 W przypadku elementów, które mają zostać uwzględnione na przykład, w kompilacji debugowania, ale nie kompilację wydania, można użyć `Condition` atrybutu, aby określić warunki, w którym należy dołączyć element.  
  
#### <a name="to-include-the-file-formulavb-only-in-release-builds"></a>Aby dołączyć plik Formula.vb tylko w kompilacjach wydania  
  
- Użyj `Condition` atrybut podobny do następującego:  
  
    ```  
    <Compile  
        Include="Formula.vb"  
        Condition=" '$(Configuration)' == 'Release' " />  
    ```  
  
## <a name="example"></a>Przykład  
 Poniższy przykład kodu tworzy projekt ze wszystkimi plikami .cs w katalogu, z wyjątkiem Form2.cs.  
  
```  
<Project DefaultTargets="Compile"  
    xmlns="http://schemas.microsoft.com/developer/msbuild/2003" >  
  
    <PropertyGroup>  
        <builtdir>built</builtdir>  
    </PropertyGroup>  
  
    <ItemGroup>  
        <CSFile Include="*.cs Exclude="Form2.cs"/>  
  
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
 [Elementy](../msbuild/msbuild-items.md)   
 [Program MSBuild](msbuild.md) [jak: Wybieranie plików do kompilacji](../msbuild/how-to-select-the-files-to-build.md)
