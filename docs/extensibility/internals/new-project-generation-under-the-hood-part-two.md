---
title: 'Generowanie nowego projektu: pod okapem, część dwie | Microsoft Docs'
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "80707020"
---
# <a name="new-project-generation-under-the-hood-part-two"></a>Generowanie nowego projektu: szczegółowe informacje (część druga)

W [obszarze Nowa generacja projektu: w obszarze okapu część,](../../extensibility/internals/new-project-generation-under-the-hood-part-one.md) w jaki sposób jest wypełniane okno dialogowe **Nowy projekt** . Załóżmy, że wybrano **aplikację systemu Windows w języku Visual C#**, wypełniono pola tekstowe **Nazwa** i **Lokalizacja** , a następnie kliknięto przycisk OK.

## <a name="generating-the-solution-files"></a>Generowanie plików rozwiązania
 Wybranie szablonu aplikacji [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] umożliwia rozpakować i otwarcie odpowiedniego pliku. vstemplate oraz uruchomienie szablonu w celu interpretacji poleceń XML w tym pliku. Te polecenia tworzą projekty i elementy projektu w nowym lub istniejącym rozwiązaniu.

 Szablon rozpakuje pliki źródłowe o nazwie szablony elementów z tego samego folderu zip, który zawiera plik. vstemplate. Szablon kopiuje te pliki do nowego projektu, odpowiednio dostosowując je.

### <a name="template-parameter-replacement"></a>Zastąpienie parametru szablonu
 Gdy szablon kopiuje szablon elementu do nowego projektu, zastępuje wszystkie parametry szablonu z ciągami, aby dostosować plik. Parametr szablonu jest specjalnym tokenem, który jest poprzedzony znakiem dolara, na przykład $date $.

 Przyjrzyjmy się typowi szablonu elementu projektu. Wyodrębnij i Przeanalizuj Program.cs w programie Files\Microsoft Visual Studio 8\Common7\IDE\ProjectTemplates\CSharp\Windows\1033\WindowsApplication.zip folder.

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

W przypadku tworzenia nowego projektu aplikacji systemu Windows o nazwie Simple szablon zastępuje `$safeprojectname$` parametr nazwą projektu.

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

## <a name="a-look-inside-a-vstemplate-file"></a>Wygląd wewnątrz. Plik VSTemplate
 Plik Basic. vstemplate ma ten format

```xml
<VSTemplate Version="2.0.0"     xmlns="http://schemas.microsoft.com/developer/vstemplate/2005"     Type="Project">
    <TemplateData>
    </TemplateData>
    <TemplateContent>
    </TemplateContent>
</VSTemplate>
```

 Szukamy \<TemplateData> sekcji w [nowej generacji projektu: pod okapem, część pierwszej](../../extensibility/internals/new-project-generation-under-the-hood-part-one.md). Tagi w tej sekcji służą do kontrolowania wyglądu okna dialogowego **Nowy projekt** .

 Tagi w \<TemplateContent> sekcji kontrolują generowanie nowych projektów i elementów projektu. Oto \<TemplateContent> sekcja z pliku cswindowsapplication. vstemplate w folderze \Program Files\Microsoft Visual Studio 8\Common7\IDE\ProjectTemplates\CSharp\Windows\1033\WindowsApplication.zip.

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

 \<Project>Tag steruje generowaniem projektu, a \<ProjectItem> tag steruje generowaniem elementu projektu. Jeśli parametr ReplaceParameters ma wartość true, szablon dostosowuje wszystkie parametry szablonu w pliku projektu lub elemencie. W takim przypadku wszystkie elementy projektu są dostosowane, z wyjątkiem Settings. Settings.

 Parametr TargetFileName określa nazwę i ścieżkę względną dla wynikającego pliku lub elementu projektu. Pozwala to na utworzenie struktury folderów dla projektu. Jeśli ten argument nie zostanie określony, element projektu będzie mieć taką samą nazwę jak szablon elementu projektu.

 Wynikowa struktura folderów aplikacji systemu Windows wygląda następująco:

 ![SimpleSolution](../../extensibility/internals/media/simplesolution.png "SimpleSolution")

 Pierwszy i jedyny \<Project> tag w szablonie odczytuje:

```xml
<Project File="WindowsApplication.csproj" ReplaceParameters="true">
```

 Powoduje to utworzenie przez nowy szablon projektu prostego pliku projektu. csproj przez skopiowanie i dostosowanie elementu szablonu pliku windowsapplication. csproj.

### <a name="designers-and-references"></a>Projektanci i odwołania
 W Eksplorator rozwiązań można zobaczyć, że folder właściwości jest obecny i zawiera oczekiwane pliki. Ale co się stało z odwołaniami projektu i zależnościami pliku projektanta, takimi jak Resources.Designer.cs do zasobów. resx i Form1.Designer.cs do Form1.cs?  Są one konfigurowane w prostym pliku. csproj, gdy zostanie wygenerowany.

 Oto element \<ItemGroup> from Simple. csproj, który tworzy odwołania do projektu:

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

 Można zobaczyć, że są to sześć odwołań do projektu, które pojawiają się w Eksplorator rozwiązań. Oto sekcja z innej \<ItemGroup> . Wiele wierszy kodu zostało usuniętych do przejrzystości. Ta sekcja Settings.Designer.cs zależy od ustawień. ustawienia:

```xml
<ItemGroup>
    <Compile Include="Properties\Settings.Designer.cs">
        <DependentUpon>Settings.settings</DependentUpon>
    </Compile>
</ItemGroup>
```

## <a name="see-also"></a>Zobacz też

- [Generowanie nowego projektu: szczegółowe informacje (część pierwsza)](../../extensibility/internals/new-project-generation-under-the-hood-part-one.md)
- [MSBuild](../../msbuild/msbuild.md)
