---
title: ProjectCollection — element (szablony Visual Studio) | Microsoft Docs
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#ProjectCollection
helpviewer_keywords:
- <ProjectCollection> element [Visual Studio Templates]
- ProjectCollection element [Visual Studio Templates]
ms.assetid: deb27180-2035-49ed-b835-c47bb3cd2f8f
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 12a22ca28c90ed1df69529ed3004b417b5e04276
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "80701977"
---
# <a name="projectcollection-element-visual-studio-templates"></a>ProjectCollection — element (szablony Visual Studio)
Określa organizację i zawartość szablonów wieloprojektowych.

 \<VSTemplate> \<TemplateContent>
 \<ProjectCollection>

## <a name="syntax"></a>Składnia

```xml
<ProjectCollection>
    <ProjectTemplateLink> ... </ProjectTemplateLink>
    <SolutionFolder> ... </SolutionFolder>
</ProjectCollection>
```

## <a name="attributes-and-elements"></a>Atrybuty i elementy
 W poniższych sekcjach opisano atrybut, elementy podrzędne i elementy nadrzędne.

### <a name="attributes"></a>Atrybuty
 Brak.

### <a name="child-elements"></a>Elementy podrzędne

|Element|Opis|
|-------------|-----------------|
|[ProjectTemplateLink](../extensibility/projecttemplatelink-element-visual-studio-templates.md)|Element opcjonalny.<br /><br /> Określa projekt w szablonie wieloprojektowym.|
|[SolutionFolder](../extensibility/solutionfolder-element-visual-studio-templates.md)|Element opcjonalny.<br /><br /> Grupowanie projektów w szablonach wieloprojektowych.|

### <a name="parent-elements"></a>Elementy nadrzędne

|Element|Opis|
|-------------|-----------------|
|[TemplateContent](../extensibility/templatecontent-element-visual-studio-templates.md)|Element wymagany.<br /><br /> Określa zawartość szablonu.|

## <a name="remarks"></a>Uwagi
 Szablony wieloprojektowe działają jak kontenery dla dwóch lub więcej projektów. `ProjectCollection`Element służy do określania projektów do uwzględnienia w szablonie. Aby uzyskać więcej informacji o szablonach wieloprojektowych, zobacz [How to: Create Project Templates](../ide/how-to-create-multi-project-templates.md).

## <a name="example"></a>Przykład
 Ten przykład pokazuje prosty plik *vstemplate* z wielojęzycznym projektem. W tym przykładzie szablon zawiera dwa projekty `My Windows Application` i `My Class Library` . `ProjectName`Atrybut w `ProjectTemplateLink` elemencie ustawia nazwę dla [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] , aby przypisać ten projekt. Jeśli `ProjectName` atrybut nie istnieje, nazwa pliku *. vstemplate* jest używana jako nazwa projektu.

```
<VSTemplate Version="3.0.0" Type="ProjectGroup"
    xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">
    <TemplateData>
        <Name>Multi-Project Template Sample</Name>
        <Description>An example of a multi-project template</Description>
        <Icon>Icon.ico</Icon>
        <ProjectType>VisualBasic</ProjectType>
    </TemplateData>
    <TemplateContent>
        <ProjectCollection>
            <ProjectTemplateLink ProjectName="My Windows Application">
                WindowsApp\MyTemplate.vstemplate
            </ProjectTemplateLink>
            <ProjectTemplateLink ProjectName="My Class Library">
                ClassLib\MyTemplate.vstemplate
            </ProjectTemplateLink>
        </ProjectCollection>
    </TemplateContent>
</VSTemplate>
```

## <a name="see-also"></a>Zobacz też
- [Odwołanie do schematu szablonu programu Visual Studio](../extensibility/visual-studio-template-schema-reference.md)
- [Tworzenie szablonów projektów i elementów](../ide/creating-project-and-item-templates.md)
- [Instrukcje: Tworzenie szablonów wieloprojektowych](../ide/how-to-create-multi-project-templates.md)
