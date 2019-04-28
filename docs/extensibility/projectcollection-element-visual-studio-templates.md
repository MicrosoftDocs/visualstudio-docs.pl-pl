---
title: Projectcollection — Element (szablony Visual Studio) | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#ProjectCollection
helpviewer_keywords:
- <ProjectCollection> element [Visual Studio Templates]
- ProjectCollection element [Visual Studio Templates]
ms.assetid: deb27180-2035-49ed-b835-c47bb3cd2f8f
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 902c2d3bf841537808317be8f196f52d23a4a64c
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62805846"
---
# <a name="projectcollection-element-visual-studio-templates"></a>Projectcollection — element (szablony Visual Studio)
Określa organizację i zawartość szablonów wieloprojektowych.

 \<VSTemplate> \<TemplateContent> \<ProjectCollection>

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
 Szablony wieloprojektowe działają jak kontenery dla dwóch lub więcej projektów. `ProjectCollection` Element jest używany do określania projekty w celu uwzględnienia w szablonie. Aby uzyskać więcej informacji o szablonach wieloprojektowych, zobacz [jak: Tworzenie szablonów wielu projektów](../ide/how-to-create-multi-project-templates.md).

## <a name="example"></a>Przykład
 W tym przykładzie pokazano prosty główny wielu projektów *.vstemplate* pliku. W tym przykładzie szablon zawiera dwa projekty `My Windows Application` i `My Class Library`. `ProjectName` Atrybutu na `ProjectTemplateLink` element ustawia nazwę [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] przypisze temu projektowi. Jeśli `ProjectName` atrybut nie istnieje, nazwa *.vstemplate* plik jest używany jako nazwa projektu.

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

## <a name="see-also"></a>Zobacz także
- [Odwołanie do schematu szablonu Visual Studio](../extensibility/visual-studio-template-schema-reference.md)
- [Tworzenie szablonów projektów i elementów](../ide/creating-project-and-item-templates.md)
- [Instrukcje: Tworzenie szablonów wielu projektów](../ide/how-to-create-multi-project-templates.md)