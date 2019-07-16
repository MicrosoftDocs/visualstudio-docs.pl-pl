---
title: Folder — Element (szablony projektu Visual Studio) | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#Folder
helpviewer_keywords:
- Folder element [Visual Studio project templates]
ms.assetid: 558e3d41-0db5-4c44-82bb-6bb87892b093
caps.latest.revision: 12
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 35448f4324213739cb2dc14a95598ac9a3d4432f
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "68204363"
---
# <a name="folder-element-visual-studio-project-templates"></a>Folder — Element (szablony projektów Visual Studio)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Określa folder, który zostanie dodany do projektu.  
  
 \<VSTemplate>  
 \<TemplateContent>  
 \<Project>  
 \<Folder>  
  
## <a name="syntax"></a>Składnia  
  
```  
<Folder Name="Project Folder">  
    <Folder> ... </Folder>  
    <ProjectItem> ... </ProjectItem>  
</Folder>  
```  
  
## <a name="attributes-and-elements"></a>Atrybuty i elementy  
 W poniższych sekcjach opisano atrybut, elementy podrzędne i elementy nadrzędne.  
  
### <a name="attributes"></a>Atrybuty  
  
|Atrybut|Opis|  
|---------------|-----------------|  
|`Name`|Atrybut wymagany.<br /><br /> Nazwa folderu projektu.|  
|`TargetFolderName`|Atrybut opcjonalny.<br /><br /> Określa nazwę do nadania folderu, gdy projekt jest tworzony na podstawie tego szablonu. Ten atrybut jest przydatne w przypadku za pomocą wymiany parametru można utworzyć nazwy folderu lub folder z ciągiem międzynarodowych nazewnictwa, który nie można użyć bezpośrednio w pliku zip.|  
  
### <a name="child-elements"></a>Elementy podrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|`Folder`|Określa folder do dodania do projektu. `Folder` elementy może zawierać podrzędnych `Folder` elementów.|  
|[ProjectItem](../extensibility/projectitem-element-visual-studio-item-templates.md)|Określa plik, aby dodać do projektu.|  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[Project](../extensibility/project-element-visual-studio-templates.md)|Opcjonalny element podrzędny elementu [TemplateContent](../extensibility/templatecontent-element-visual-studio-templates.md).|  
  
## <a name="remarks"></a>Uwagi  
 `Folder` jest podrzędnym opcjonalne `Project`.  
  
 Do organizowania elementów projektu w foldery w szablonie, można użyć dowolnej z następujących metod:  
  
- Będą one wyświetlane w pliku zip szablonu i dodać je do projektu w pliku .vstemplate, określając ścieżkę do pliku w `ProjectItem` elementów, na których nie `Folder` elementów. Jest to zalecana metoda. Przykład:  
  
     `...`  
  
     `<ProjectItem>\Folder\item.cs</ProjectItem>`  
  
     `<ProjectItem>Form1.cs</ProjectItem>`  
  
     `...`  
  
- Będą one wyświetlane w pliku zip szablonu i dodaj je do projektu w pliku .vstemplate z `Folder` elementów. Na przykład:  
  
     `...`  
  
     `<Folder name="Folder">`  
  
     `<ProjectItem>item.cs</ProjectItem>`  
  
     `</Folder>`  
  
     `<ProjectItem>Form1.cs</ProjectItem>`  
  
     `...`  
  
- Nie dołączaj folderów w pliku zip szablonu, ale Dodaj folderów za pomocą `TargetFileName` atrybutu `ProjectItem` elementu. Na przykład:  
  
     `...`  
  
     `<ProjectItem TargetFileName="\Folder\item.cs">item.cs</ProjectItem>`  
  
     `<ProjectItem>Form1.cs</ProjectItem>`  
  
     `...`  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie pokazano metadanych szablon projektu służący do [!INCLUDE[csprcs](../includes/csprcs-md.md)] aplikacji Windows.  
  
```  
<VSTemplate Type="Project" Version="3.0.0"  
    xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">  
    <TemplateData>  
        <Name>My template</Name>  
        <Description>A basic template</Description>  
        <Icon>TemplateIcon.ico</Icon>  
        <ProjectType>CSharp</ProjectType>  
    </TemplateData>  
    <TemplateContent>  
        <Project File="MyTemplate.csproj">  
            <ProjectItem>Form1.cs<ProjectItem>  
            <ProjectItem>Form1.Designer.cs</ProjectItem>  
            <ProjectItem>Program.cs</ProjectItem>  
            <Folder Name="Properties">  
                <ProjectItem>AssemblyInfo.cs</ProjectItem>  
                <ProjectItem>Resources.resx</ProjectItem>  
                <ProjectItem>Resources.Designer.cs</ProjectItem>  
                <ProjectItem>Settings.settings</ProjectItem>  
                <ProjectItem>Settings.Designer.cs</ProjectItem>  
            </Folder>  
        </Project>  
    </TemplateContent>  
</VSTemplate>  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Odwołanie do schematu szablonu Visual Studio](../extensibility/visual-studio-template-schema-reference.md)   
 [Tworzenie szablonów projektów i elementów](../ide/creating-project-and-item-templates.md)   
 [ProjectItem, element (szablony elementów Visual Studio)](../extensibility/projectitem-element-visual-studio-item-templates.md)
