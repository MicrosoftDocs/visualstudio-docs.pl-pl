---
title: Folder — element (szablony projektów Visual Studio) | Microsoft Docs
description: Dowiedz się więcej na temat elementu folderu i sposobu określania folderu, który zostanie dodany do projektu.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#Folder
helpviewer_keywords:
- Folder element [Visual Studio project templates]
ms.assetid: 558e3d41-0db5-4c44-82bb-6bb87892b093
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 9b655308760d64f97c168e8000972142f159ec3a
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99968232"
---
# <a name="folder-element-visual-studio-project-templates"></a>Folder — element (szablony projektów Visual Studio)
Określa folder, który zostanie dodany do projektu.

 \<VSTemplate> \<TemplateContent>
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
|`TargetFolderName`|Atrybut opcjonalny.<br /><br /> Określa nazwę do nadania folderowi, gdy projekt jest tworzony na podstawie szablonu. Ten atrybut jest przydatny do tworzenia nazwy folderu lub nazywania folderu za pomocą międzynarodowego ciągu, którego nie można użyć bezpośrednio w pliku *zip* .|

### <a name="child-elements"></a>Elementy podrzędne

|Element|Opis|
|-------------|-----------------|
|`Folder`|Określa folder, który ma zostać dodany do projektu. `Folder` elementy mogą zawierać `Folder` elementy podrzędne.|
|[ProjectItem](../extensibility/projectitem-element-visual-studio-item-templates.md)|Określa plik, który ma zostać dodany do projektu.|

### <a name="parent-elements"></a>Elementy nadrzędne

|Element|Opis|
|-------------|-----------------|
|[Project](../extensibility/project-element-visual-studio-templates.md)|Opcjonalny element podrzędny elementu [TemplateContent](../extensibility/templatecontent-element-visual-studio-templates.md).|

## <a name="remarks"></a>Uwagi
 `Folder` jest opcjonalnym elementem podrzędnym `Project` .

 Można użyć dowolnej z poniższych metod, aby zorganizować elementy projektu w foldery w szablonie:

- Uwzględnij foldery w pliku template *. zip* i Dodaj je do projektu w pliku *. vstemplate* , określając ścieżkę do pliku w `ProjectItem` elementach, bez `Folder` elementów. Jest to zalecana metoda. Na przykład:

     `...`

     `<ProjectItem>\Folder\item.cs</ProjectItem>`

     `<ProjectItem>Form1.cs</ProjectItem>`

     `...`

- Uwzględnij foldery w pliku template *. zip* i Dodaj je do projektu w pliku *vstemplate* z `Folder` elementami. Na przykład:

     `...`

     `<Folder name="Folder">`

     `<ProjectItem>item.cs</ProjectItem>`

     `</Folder>`

     `<ProjectItem>Form1.cs</ProjectItem>`

     `...`

- Nie dołączaj folderów do pliku template *. zip* , ale Dodaj foldery przy użyciu `TargetFileName` atrybutu `ProjectItem` elementu. Na przykład:

     `...`

     `<ProjectItem TargetFileName="\Folder\item.cs">item.cs</ProjectItem>`

     `<ProjectItem>Form1.cs</ProjectItem>`

     `...`

## <a name="example"></a>Przykład
 Poniższy przykład ilustruje metadane szablonu projektu dla [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] aplikacji systemu Windows.

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
- [ProjectItem, element (szablony elementów Visual Studio)](../extensibility/projectitem-element-visual-studio-item-templates.md)
