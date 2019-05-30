---
title: Folder — Element (szablony projektu Visual Studio) | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: conceptual
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#Folder
helpviewer_keywords:
- Folder element [Visual Studio project templates]
ms.assetid: 558e3d41-0db5-4c44-82bb-6bb87892b093
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 6c066bfacea4996ab8d212ac607a3dfa3f3fad36
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/29/2019
ms.locfileid: "66342612"
---
# <a name="folder-element-visual-studio-project-templates"></a>Folder — element (szablony projektu Visual Studio)
Określa folder, który zostanie dodany do projektu.

 \<VSTemplate> \<TemplateContent> \<Project> \<Folder>

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
|`TargetFolderName`|Atrybut opcjonalny.<br /><br /> Określa nazwę do nadania folderu, gdy projekt jest tworzony na podstawie tego szablonu. Ten atrybut jest przydatne w przypadku za pomocą wymiany parametru można utworzyć nazwy folderu lub folder z ciągiem międzynarodowych nazewnictwa, który nie można użyć bezpośrednio w *zip* pliku.|

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

- Dołącz foldery w szablonie *zip* plik i dodać je do projektu w *.vstemplate* pliku, określając ścieżkę do pliku w `ProjectItem` elementów, na których nie `Folder` elementów. Jest to zalecana metoda. Na przykład:

     `...`

     `<ProjectItem>\Folder\item.cs</ProjectItem>`

     `<ProjectItem>Form1.cs</ProjectItem>`

     `...`

- Dołącz foldery w szablonie *zip* plik i dodać je do projektu w *.vstemplate* plik z `Folder` elementów. Na przykład:

     `...`

     `<Folder name="Folder">`

     `<ProjectItem>item.cs</ProjectItem>`

     `</Folder>`

     `<ProjectItem>Form1.cs</ProjectItem>`

     `...`

- Nie dołączaj folderów w szablonie *zip* plików, ale Dodaj folderów za pomocą `TargetFileName` atrybutu `ProjectItem` elementu. Na przykład:

     `...`

     `<ProjectItem TargetFileName="\Folder\item.cs">item.cs</ProjectItem>`

     `<ProjectItem>Form1.cs</ProjectItem>`

     `...`

## <a name="example"></a>Przykład
 W poniższym przykładzie pokazano metadanych szablon projektu służący do [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] aplikacji Windows.

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

## <a name="see-also"></a>Zobacz także
- [Odwołanie do schematu szablonu Visual Studio](../extensibility/visual-studio-template-schema-reference.md)
- [Tworzenie szablonów projektów i elementów](../ide/creating-project-and-item-templates.md)
- [Projectitem — element (szablony elementów Visual Studio)](../extensibility/projectitem-element-visual-studio-item-templates.md)