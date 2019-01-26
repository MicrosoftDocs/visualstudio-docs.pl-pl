---
title: 'Generowanie nowego projektu: Za kulisami, część dwóch | Dokumentacja firmy Microsoft'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- projects [Visual Studio], new project dialog
- projects [Visual Studio], new project generation
ms.assetid: 73ce91d8-0ab1-4a1f-bf12-4d3c49c01e13
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: d0a22adb627edcbda6f823c659b20f41524b83a8
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/25/2019
ms.locfileid: "54949028"
---
# <a name="new-project-generation-under-the-hood-part-two"></a>Generowanie nowego projektu: Kulisami część druga
W [Generowanie nowego projektu: Kulisami, część 1](../../extensibility/internals/new-project-generation-under-the-hood-part-one.md) widzieliśmy sposób, w jaki **nowy projekt** okna dialogowego pole zostanie wypełnione. Załóżmy, że wybrano **Visual C# Windows Application**, wypełnionego **nazwa** i **lokalizacji** pola tekstowe i kliknięto OK.  
  
## <a name="generating-the-solution-files"></a>Generowanie plików rozwiązania  
 Wybieranie szablonu aplikacji kieruje [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Rozpakowywanie i otwieranie odpowiedni plik .vstemplate i uruchom szablon, aby zinterpretować poleceń XML w tym pliku. Te polecenia powodują utworzenie projektów i elementów projektu w nowym lub istniejącym rozwiązaniu.  
  
 Szablon wypakowuje plików źródłowych, o nazwie szablonów elementów z tego samego folderu zip, który zawiera plik .vstemplate. Ten szablon kopiuje te pliki do nowego projektu, dostosowywanie ich odpowiednio.  
  
### <a name="template-parameter-replacement"></a>Zastąpienie parametru szablonu  
 Gdy szablon kopiuje szablon elementu do nowego projektu, zastępuje wszelkie parametry szablonu z ciągami, aby dostosować plik. Parametr szablonu ma specjalne token, który jest poprzedzony i następuje znak dolara, na przykład, $date$.  
  
 Przyjrzyjmy się szablon elementu typowym projekcie. Wyodrębnianie i sprawdź plik Program.cs w folderze Program Files\Microsoft Visual Studio 8\Common7\IDE\ProjectTemplates\CSharp\Windows\1033\WindowsApplication.zip.  
  
```  
using System;  
using System.Collections.Generic;  
using System.Windows.Forms;  
  
namespace $safeprojectname$  
{  
    static class Program  
    {  
        // source code deleted here for brevity  
    }  
}  
```  
  
 Jeśli tworzysz nowy projekt aplikacji Windows o nazwie prosty, szablon zastępuje `$safeprojectname$` parametr o nazwie projektu.  
  
```  
using System;  
using System.Collections.Generic;  
using System.Windows.Forms;  
  
namespace Simple  
{  
    static class Program  
    {  
        // source code deleted here for brevity  
    }  
}  
```  
  
 Aby uzyskać pełną listę parametrów szablonu, zobacz [parametry szablonu](../../ide/template-parameters.md).  
  
## <a name="a-look-inside-a-vstemplate-file"></a>Wygląd wewnątrz. Plik VSTemplate  
 Ten format jest plik .vstemplate podstawowe  
  
```  
<VSTemplate Version="2.0.0"     xmlns="http://schemas.microsoft.com/developer/vstemplate/2005"     Type="Project">  
    <TemplateData>  
    </TemplateData>  
    <TemplateContent>  
    </TemplateContent>  
</VSTemplate>  
```  
  
 Zobaczyliśmy \<TemplateData > sekcji [Generowanie nowego projektu: Za kulisami, część jednego](../../extensibility/internals/new-project-generation-under-the-hood-part-one.md). Znaczniki w tej sekcji są używane do kontrolowania wygląd **nowy projekt** okno dialogowe.  
  
 Znaczniki \<TemplateContent > sekcji kontroli Generowanie nowych projektów i elementów projektu. Oto \<TemplateContent > sekcji z pliku cswindowsapplication.vstemplate w folderze 8\Common7\IDE\ProjectTemplates\CSharp\Windows\1033\WindowsApplication.zip \Program Files\Microsoft programu Visual Studio.  
  
```  
<TemplateContent>  
  <Project File="WindowsApplication.csproj" ReplaceParameters="true">  
    <ProjectItem ReplaceParameters="true"  
      TargetFileName="Properties\AssemblyInfo.cs">  
      AssemblyInfo.cs  
    </ProjectItem>  
    <ProjectItem TargetFileName="Properties\Resources.resx">  
      Resources.resx  
    </ProjectItem>  
    <ProjectItem ReplaceParameters="true"       TargetFileName="Properties\Resources.Designer.cs">  
      Resources.Designer.cs  
    </ProjectItem>  
    <ProjectItem TargetFileName="Properties\Settings.settings">  
      Settings.settings  
    </ProjectItem>  
    <ProjectItem ReplaceParameters="true"       TargetFileName="Properties\Settings.Designer.cs">  
      Settings.Designer.cs  
    </ProjectItem>  
    <ProjectItem ReplaceParameters="true" OpenInEditor="true">  
      Form1.cs  
    </ProjectItem>  
    <ProjectItem ReplaceParameters="true">  
      Form1.Designer.cs  
    </ProjectItem>  
    <ProjectItem ReplaceParameters="true">  
      Program.cs  
    </ProjectItem>  
  </Project>  
</TemplateContent>  
```  
  
 \<Projekt > tag kontroluje Generowanie projektu i \<ProjectItem > tag kontroluje Generowanie elementu projektu. Jeśli parametr ReplaceParameters ma wartość true, szablon umożliwia dostosowywanie wszystkich parametrów szablonu w pliku projektu lub elementu. W takim przypadku wszystkie elementy projektu są dostosowywane, z wyjątkiem Settings.settings.  
  
 Parametr TargetFileName Określa nazwę i ścieżkę względną, wynikowy plik projektu lub elementu. Dzięki temu można utworzyć strukturę folderów dla Twojego projektu. Jeśli nie określisz tego argumentu, elementu projektu będzie mieć taką samą nazwę jak szablonu elementu projektu.  
  
 Wynikowy strukturę folderów aplikacji Windows wygląda następująco:  
  
 ![SimpleSolution](../../extensibility/internals/media/simplesolution.png "SimpleSolution")  
  
 Pierwszą i jedyną \<Projekt > tag w odczyty szablonu:  
  
```  
<Project File="WindowsApplication.csproj" ReplaceParameters="true">  
```  
  
 To powoduje, że szablon nowy projekt, aby utworzyć plik projektu Simple.csproj, kopiowanie i dostosowując windowsapplication.csproj element szablonu.  
  
### <a name="designers-and-references"></a>Projektanci i odwołań  
 Widoczne w Eksploratorze rozwiązań, w folderze właściwości jest dostępny i zawiera oczekiwane pliki. Ale co projekt odwołuje się i zależności pliku projektanta, takie jak Resources.Designer.cs do Resources.resx i Form1.Designer.cs się Form1.cs?  Te właściwości są ustawiane w pliku Simple.csproj po jego wygenerowaniu.  
  
 Oto \<ItemGroup > z Simple.csproj, który tworzy odwołania do projektu:  
  
```  
<ItemGroup>  
    <Reference Include="System" />  
    <Reference Include="System.Data" />  
    <Reference Include="System.Deployment" />  
    <Reference Include="System.Drawing" />  
    <Reference Include="System.Windows.Forms" />  
    <Reference Include="System.Xml" />  
</ItemGroup>  
```  
  
 Widać, że są one odwołań sześć projektu, które są wyświetlane w Eksploratorze rozwiązań. Poniżej przedstawiono sekcję z innego \<ItemGroup >. Wiele wierszy kodu zostały usunięte w celu uściślenia. W tej sekcji sprawia, że Settings.Designer.cs jest zależny od Settings.settings:  
  
```  
<ItemGroup>  
    <Compile Include="Properties\Settings.Designer.cs">  
        <DependentUpon>Settings.settings</DependentUpon>  
    </Compile>  
</ItemGroup>  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Generowanie nowego projektu: Kulisami część pierwsza](../../extensibility/internals/new-project-generation-under-the-hood-part-one.md)  
 [MSBuild](../../msbuild/msbuild.md)