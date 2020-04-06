---
title: 'Nowa generacja projektów: Pod maską, część druga | Dokumenty firmy Microsoft'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- projects [Visual Studio], new project dialog
- projects [Visual Studio], new project generation
ms.assetid: 73ce91d8-0ab1-4a1f-bf12-4d3c49c01e13
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 8692f2012e5f2733982f04e35a7fed415e49c636
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80707020"
---
# <a name="new-project-generation-under-the-hood-part-two"></a>Generowanie nowego projektu: za kulisami, część druga

W [nowej generacji projektu: Pod maską, część pierwsza widzieliśmy,](../../extensibility/internals/new-project-generation-under-the-hood-part-one.md) jak okno dialogowe Nowy **projekt** jest wypełniona. Załóżmy, że wybrano **aplikację systemu Windows visual c#,** wypełniliśmy pola tekstowe **Nazwa** i **lokalizacja** i kliknięno przycisk OK.

## <a name="generating-the-solution-files"></a>Generowanie plików rozwiązania
 Wybranie [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] szablonu aplikacji powoduje nakipowanie i otwarcie odpowiedniego pliku vstemplate oraz uruchomienie szablonu do interpretacji poleceń XML w tym pliku. Te polecenia tworzą projekty i elementy projektu w nowym lub istniejącym rozwiązaniu.

 Szablon rozpakowuje pliki źródłowe, zwane szablonami elementów, z tego samego folderu .zip, w którego znajduje się plik vstemplate. Szablon kopiuje te pliki do nowego projektu, dostosowując je odpowiednio.

### <a name="template-parameter-replacement"></a>Zastępowanie parametrów szablonu
 Gdy szablon kopiuje szablon elementu do nowego projektu, zastępuje wszystkie parametry szablonu ciągami znaków, aby dostosować plik. Parametr szablonu to specjalny token, który jest poprzedzony i następuje znak dolara, na przykład $date$.

 Przyjrzyjmy się typowej szablonu elementu projektu. Wyodrębnianie i badanie Program.cs w folderze Program Files\Microsoft Visual Studio 8\Common7\IDE\ProjectTemplates\CSharp\Windows\1033\WindowsApplication.zip folder.

```csharp
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

Jeśli utworzysz nowy projekt aplikacji systemu Windows `$safeprojectname$` o nazwie Simple, szablon zastępuje parametr nazwą projektu.

```csharp
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

 Aby uzyskać pełną listę parametrów szablonu, zobacz [Parametry szablonu](../../ide/template-parameters.md).

## <a name="a-look-inside-a-vstemplate-file"></a>Spojrzenie wewnątrz . Plik VSTemplate
 Podstawowy plik .vstemplate ma ten format

```xml
<VSTemplate Version="2.0.0"     xmlns="http://schemas.microsoft.com/developer/vstemplate/2005"     Type="Project">
    <TemplateData>
    </TemplateData>
    <TemplateContent>
    </TemplateContent>
</VSTemplate>
```

 Przyjrzeliśmy się \<sekcji TemplateData> w [nowej generacji projektu: Pod maską, część pierwsza](../../extensibility/internals/new-project-generation-under-the-hood-part-one.md). Znaczniki w tej sekcji służą do kontrolowania wyglądu okna dialogowego **Nowy projekt.**

 Znaczniki w \<sekcji TemplateContent> kontrolują generowanie nowych projektów i elementów projektu. Oto sekcja \<TemplateContent> z pliku cswindowsapplication.vstemplate w folderze \Program Files\Microsoft Visual Studio 8\Common7\IDE\ProjectTemplates\CSharp\Windows\1033\WindowsApplication.zip folder.

```xml
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

 Tag \<> projektu steruje generowaniem projektu, a \<tag> ProjectItem steruje generowaniem elementu projektu. Jeśli parametr ReplaceParameters jest spełniony, szablon dostosuje wszystkie parametry szablonu w pliku lub elemencie projektu. W takim przypadku wszystkie elementy projektu są dostosowywane, z wyjątkiem Settings.settings.

 Parametr TargetFileName określa nazwę i ścieżkę względną wynikowego pliku lub elementu projektu. Dzięki temu można utworzyć strukturę folderów dla projektu. Jeśli ten argument nie zostanie określony, element projektu będzie miał taką samą nazwę jak szablon elementu projektu.

 Wynikowa struktura folderów aplikacji systemu Windows wygląda następująco:

 ![Prostąrozdzielę](../../extensibility/internals/media/simplesolution.png "Prostąrozdzielę")

 Pierwszy i \<jedyny tag> programu Project w szablonie brzmi:

```xml
<Project File="WindowsApplication.csproj" ReplaceParameters="true">
```

 Nakazuje szablonowi Nowy projekt utworzenie pliku projektu Simple.csproj przez skopiowanie i dostosowanie elementu szablonu windowsapplication.csproj.

### <a name="designers-and-references"></a>Projektanci i referencje
 W Eksploratorze rozwiązań widać, że folder Właściwości jest obecny i zawiera oczekiwane pliki. Ale co z odwołaniami do projektu i zależnościami plików projektanta, takimi jak Resources.Designer.cs do pliku Resources.resx i Form1.Designer.cs do Form1.cs?  Są one konfigurajne w pliku Simple.csproj, gdy jest generowany.

 Oto \<itemgroup> z Simple.csproj, który tworzy odwołania do projektu:

```xml
<ItemGroup>
    <Reference Include="System" />
    <Reference Include="System.Data" />
    <Reference Include="System.Deployment" />
    <Reference Include="System.Drawing" />
    <Reference Include="System.Windows.Forms" />
    <Reference Include="System.Xml" />
</ItemGroup>
```

 Widać, że są to sześć odwołań do projektu, które pojawiają się w Eksploratorze rozwiązań. Oto sekcja z innego \<> ItemGroup. Wiele wierszy kodu zostały usunięte dla jasności. W tej sekcji Settings.Designer.cs zależy od ustawienia.settings:

```xml
<ItemGroup>
    <Compile Include="Properties\Settings.Designer.cs">
        <DependentUpon>Settings.settings</DependentUpon>
    </Compile>
</ItemGroup>
```

## <a name="see-also"></a>Zobacz też

- [Generowanie nowego projektu: za kulisami, część pierwsza](../../extensibility/internals/new-project-generation-under-the-hood-part-one.md)
- [MSBuild](../../msbuild/msbuild.md)
