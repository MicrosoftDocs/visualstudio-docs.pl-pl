---
title: Element folderu (szablony projektów programu Visual Studio) | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: conceptual
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#Folder
helpviewer_keywords:
- Folder element [Visual Studio project templates]
ms.assetid: 558e3d41-0db5-4c44-82bb-6bb87892b093
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: cb256b8be0dd9ce68f193750bf3ff5a383d5f073
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80711464"
---
# <a name="folder-element-visual-studio-project-templates"></a>Element folderu (szablony projektów programu Visual Studio)
Określa folder, który zostanie dodany do projektu.

 \<> \<> folder \< \<>> projektu>

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
|`TargetFolderName`|Atrybut opcjonalny.<br /><br /> Określa nazwę, która ma nadać folderowi podczas tworzenia projektu na podstawie szablonu. Ten atrybut jest przydatny do tworzenia nazwy folderu przy użyciu zastępowania parametrów lub nazywania folderu ciągiem międzynarodowym, którego nie można używać bezpośrednio w pliku *zip.*|

### <a name="child-elements"></a>Elementy podrzędne

|Element|Opis|
|-------------|-----------------|
|`Folder`|Określa folder, który ma być dodawany do projektu. `Folder`elementy mogą `Folder` zawierać elementy podrzędne.|
|[ProjectItem](../extensibility/projectitem-element-visual-studio-item-templates.md)|Określa plik, który ma być dodawany do projektu.|

### <a name="parent-elements"></a>Elementy nadrzędne

|Element|Opis|
|-------------|-----------------|
|[Projekt](../extensibility/project-element-visual-studio-templates.md)|Opcjonalny element podrzędny [TemplateContent](../extensibility/templatecontent-element-visual-studio-templates.md).|

## <a name="remarks"></a>Uwagi
 `Folder`jest opcjonalnym `Project`dzieckiem .

 Do organizowania elementów projektu w folderach w szablonie można użyć dowolnej z następujących metod:

- Dołącz foldery do pliku *.zip* szablonu i dodaj je do projektu w pliku *vstemplate,* `ProjectItem` określając ścieżkę `Folder` do pliku w elementach, bez elementów. Jest to zalecana metoda. Przykład:

     `...`

     `<ProjectItem>\Folder\item.cs</ProjectItem>`

     `<ProjectItem>Form1.cs</ProjectItem>`

     `...`

- Dołącz foldery do pliku *zip* szablonu i dodaj je do projektu w pliku `Folder` *vstemplate* z elementami. Przykład:

     `...`

     `<Folder name="Folder">`

     `<ProjectItem>item.cs</ProjectItem>`

     `</Folder>`

     `<ProjectItem>Form1.cs</ProjectItem>`

     `...`

- Nie dołączaj folderów do pliku *zip* szablonu, `TargetFileName` ale dodaj `ProjectItem` foldery przy użyciu atrybutu elementu. Przykład:

     `...`

     `<ProjectItem TargetFileName="\Folder\item.cs">item.cs</ProjectItem>`

     `<ProjectItem>Form1.cs</ProjectItem>`

     `...`

## <a name="example"></a>Przykład
 Poniższy przykład ilustruje metadane dla [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] szablonu projektu dla aplikacji systemu Windows.

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
- [Odwołanie do schematu szablonu programu Visual Studio](../extensibility/visual-studio-template-schema-reference.md)
- [Tworzenie szablonów projektów i elementów](../ide/creating-project-and-item-templates.md)
- [Element ProjectItem (szablony elementów programu Visual Studio)](../extensibility/projectitem-element-visual-studio-item-templates.md)
