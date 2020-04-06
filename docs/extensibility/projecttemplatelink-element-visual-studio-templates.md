---
title: Element ProjectTemplateLink (szablony programu Visual Studio) | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#ProjectTemplateLink
helpviewer_keywords:
- <ProjectTemplateLink> element [Visual Studio Templates]
- ProjectTemplateLink element [Visual Studio Templates]
ms.assetid: b0449111-8b48-45a1-a031-ea24b765e969
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: e6d402b6605f2e01a20d400c2c33573c686a1cdd
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80701820"
---
# <a name="projecttemplatelink-element-visual-studio-templates"></a>Element ProjectTemplateLink (szablony programu Visual Studio)
Określa ścieżkę do pliku *vstemplate* jednego projektu w szablonie wieloprojektowym.

 \<\<VSTemplate> TemplateContent> \<ProjectCollection> \<ProjectTemplateLink> - lub- \<VSTemplate> \<templateContent> \<ProjectCollection> \<SolutionFolder> \<ProjectTemplateLink>

## <a name="syntax"></a>Składnia

```xml
<ProjectTemplateLink ProjectName="Name">
    PathToTemplateFile
</ProjectTemplateLink>
```

## <a name="attributes-and-elements"></a>Atrybuty i elementy
 W poniższych sekcjach opisano atrybut, elementy podrzędne i elementy nadrzędne.

### <a name="attributes"></a>Atrybuty

|Atrybut|Opis|
|---------------|-----------------|
|`ProjectName`|Atrybut opcjonalny.<br /><br /> Określa nazwę każdego indywidualnego projektu w szablonie wieloprojektowym. Okno dialogowe **Nowy projekt** nie może przypisywać nazw do poszczególnych projektów.|
|`CopyParameters`|Umożliwia kopiowanie wszystkich zmiennych z głównego szablonu grupowego do poszczególnych połączonych szablonów.<br /><br /> Parametry w połączonych szablonach mają `"$ext_*$"`prefiks . Na przykład jeśli w szablonie `$projectname$` grupy nadrzędnej parametr ma wartość **ExampleProject1**, gdy połączony szablon `$ext_projectname$`pobiera jego kolej do `$projectname$` wykonania, uzyskuje parametr , który jest kopią parametru z szablonu grupy nadrzędnej.<br /><br /> Dzięki temu połączone szablony mogą korzystać z niektórych wspólnych parametrów tworzonych wygodnie tylko w nadrzędnym szablonie grupowym.<br /><br /> Ten atrybut jest opcjonalny i automatycznie `false` domyślnie, gdy nie jest uwzględniony.<br /><br /> Wprowadzono w programie Visual Studio 2013 Aktualizacja 2. Aby odwołać się do poprawnej wersji produktu, zobacz [Zestawy odwołań dostarczone w aktualizacji SDK programu Visual Studio 2013 2](https://msdn.microsoft.com/library/42b65c3e-e42b-4c39-98c8-bea285f25ffb).|

### <a name="child-elements"></a>Elementy podrzędne
 Brak.

### <a name="parent-elements"></a>Elementy nadrzędne

|Element|Opis|
|-------------|-----------------|
|[ProjectCollection](../extensibility/projectcollection-element-visual-studio-templates.md)|Określa organizację i zawartość szablonów wieloprojektowych.|
|[SolutionFolder](../extensibility/solutionfolder-element-visual-studio-templates.md)|Grupowanie projektów w szablonach wieloprojektowych.|

## <a name="text-value"></a>Wartość tekstowa
 Wartość tekstowa jest wymagana.

 Ten tekst określa ścieżkę do pliku *vstemplate* szablonu.

## <a name="remarks"></a>Uwagi
 Szablony wieloprojektowe działają jak kontenery dla dwóch lub więcej projektów. Element `ProjectTemplateLink` jest używany do określenia lokalizacji pliku *vstemplate* dla jednego z projektów w szablonie. Plik *vstemplate* szablonu wielu projektów zawiera `ProjectTemplateLink` jeden element dla każdego projektu w szablonie. Aby uzyskać więcej informacji na temat szablonów wielu projektów, zobacz [Jak: Tworzenie szablonów wielu projektów](../ide/how-to-create-multi-project-templates.md).

## <a name="example"></a>Przykład
 W tym przykładzie pokazano prosty plik *.vstemplate* root multi-project. W tym przykładzie szablon zawiera `My Windows Application` `My Class Library`dwa projekty i . Atrybut `ProjectName` w elemencie `ProjectTemplateLink` ustawia [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] nazwę, aby przypisać ten projekt. Jeśli `ProjectName` atrybut nie istnieje, nazwa pliku *vstemplate* jest używana jako nazwa projektu.

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
            <ProjectTemplateLink ProjectName="My Class Library" CopyParameters="true">
                ClassLib\MyTemplate.vstemplate
            </ProjectTemplateLink>
        </ProjectCollection>
    </TemplateContent>
</VSTemplate>
```

## <a name="see-also"></a>Zobacz też
- [Odwołanie do schematu szablonu programu Visual Studio](../extensibility/visual-studio-template-schema-reference.md)
- [Tworzenie szablonów projektów i elementów](../ide/creating-project-and-item-templates.md)
- [Jak: Tworzenie szablonów wielu projektów](../ide/how-to-create-multi-project-templates.md)
