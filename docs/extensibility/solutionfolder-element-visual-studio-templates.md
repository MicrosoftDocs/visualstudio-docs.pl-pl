---
title: Solutionfolder — Element (szablony Visual Studio) | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#SolutionFolder
helpviewer_keywords:
- <SolutionFolder> element [Visual Studio Templates]
- SolutionFolder element [Visual Studio Templates]
ms.assetid: 963f0398-fb50-4d8e-879d-d48f8b7c6d80
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 4fd2ce948a3e18633f4c9875fa3ec0b064a91b35
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/29/2019
ms.locfileid: "66331993"
---
# <a name="solutionfolder-element-visual-studio-templates"></a>SolutionFolder — Element (szablony Visual Studio)
Grupowanie projektów w szablonach wieloprojektowych.

 \<VSTemplate> \<TemplateContent> \<ProjectCollection> \<SolutionFolder>

## <a name="syntax"></a>Składnia

```
<SolutionFolder Name="DirectoryName">
    ...
</SolutionFolder>
```

## <a name="attributes-and-elements"></a>Atrybuty i elementy
 W poniższych sekcjach opisano atrybut, elementy podrzędne i elementy nadrzędne.

### <a name="attributes"></a>Atrybuty

|Atrybut|Opis|
|---------------|-----------------|
|`Name`|Atrybut wymagany.<br /><br /> Nazwa folderu rozwiązania.|

### <a name="child-elements"></a>Elementy podrzędne

|Element|Opis|
|-------------|-----------------|
|[ProjectTemplateLink](../extensibility/projecttemplatelink-element-visual-studio-templates.md)|Element opcjonalny.<br /><br /> Określa ścieżkę do pliku .vstemplate jednego projektu w szablonie wieloprojektowym.|
|`SolutionFolder`|Element opcjonalny.<br /><br /> Grupowanie projektów w szablonach wieloprojektowych.|

### <a name="parent-elements"></a>Elementy nadrzędne

|Element|Opis|
|-------------|-----------------|
|[ProjectCollection](../extensibility/projectcollection-element-visual-studio-templates.md)|Określa organizację i zawartość szablonów wieloprojektowych.|
|`SolutionFolder`|Grupowanie projektów w szablonach wieloprojektowych.|

## <a name="remarks"></a>Uwagi
 Szablony wieloprojektowe działają jak kontenery dla dwóch lub więcej projektów. `SolutionFolder` Element służy do organizowania projektów w szablonie w grupy. Foldery określone przez `SolutionFolder` elementy są tworzone jako folderów rozwiązania, projektu w [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. Aby uzyskać więcej informacji o szablonach wieloprojektowych, zobacz [jak: Tworzenie szablonów wielu projektów](../ide/how-to-create-multi-project-templates.md).

## <a name="example"></a>Przykład
 W tym przykładzie użyto `SolutionFolder` elementu, aby podzielić szablonu wieloprojektowego na dwie grupy `Math Classes` i `Graphics Classes`. Szablon zawiera cztery projektów, dwie z nich są umieszczane w każdym folderze rozwiązania.

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
            <SolutionFolder Name="Math Classes">
                <ProjectTemplateLink ProjectName="MathClassLib1">
                    MathClassLib1\MyTemplate.vstemplate
                </ProjectTemplateLink>
                <ProjectTemplateLink ProjectName="MathClassLib2">
                    MathClassLib2\MyTemplate.vstemplate
                </ProjectTemplateLink>
            </SolutionFolder>
            <SolutionFolder Name="Graphics Classes">
                <ProjectTemplateLink ProjectName="GraphicsClassLib1">
                    GraphicsClassLib1\MyTemplate.vstemplate
                </ProjectTemplateLink>
                <ProjectTemplateLink ProjectName="GraphicsClassLib2">
                    GraphicsClassLib2\MyTemplate.vstemplate
                </ProjectTemplateLink>
            </SolutionFolder>
        </ProjectCollection>
    </TemplateContent>
</VSTemplate>
```

## <a name="see-also"></a>Zobacz też
- [Odwołanie do schematu szablonu Visual Studio](../extensibility/visual-studio-template-schema-reference.md)
- [Tworzenie szablonów projektu i elementu](../ide/creating-project-and-item-templates.md)
- [Instrukcje: Tworzenie szablonów obejmujących wiele projektów](../ide/how-to-create-multi-project-templates.md)