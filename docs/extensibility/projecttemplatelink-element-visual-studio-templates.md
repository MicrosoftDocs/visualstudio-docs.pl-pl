---
title: Projecttemplatelink — Element (szablony Visual Studio) | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#ProjectTemplateLink
helpviewer_keywords:
- <ProjectTemplateLink> element [Visual Studio Templates]
- ProjectTemplateLink element [Visual Studio Templates]
ms.assetid: b0449111-8b48-45a1-a031-ea24b765e969
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 3bc253967cf4f52d6e958b8b092f44f753bac2e9
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/22/2019
ms.locfileid: "56698095"
---
# <a name="projecttemplatelink-element-visual-studio-templates"></a>ProjectTemplateLink element (Visual Studio templates)
Określa ścieżkę do *.vstemplate* pliku jednego projektu w szablonie wieloprojektowym.

 \<VSTemplate> \<TemplateContent> \<ProjectCollection> \<ProjectTemplateLink> -or- \<VSTemplate> \<TemplateContent> \<ProjectCollection> \<SolutionFolder> \<ProjectTemplateLink>

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
|`ProjectName`|Atrybut opcjonalny.<br /><br /> Określa nazwę każdego indywidualnego projektu w szablonie wieloprojektowym. **Nowy projekt** okno dialogowe nie można przypisywać nazw poszczególnym projektom.|
|`CopyParameters`|Umożliwia kopiowanie wszystkich zmiennych z głównego szablonu grupowego do poszczególnych połączonych szablonów.<br /><br /> Parametry w połączonych szablonach mają prefiks `"$ext_*$"`. Na przykład, jeśli w nadrzędnym szablonie grupowym parametr `$projectname$` ma wartość **ExampleProject1**, gdy połączony szablon pobiera swoją kolej, aby można było wykonywane, parametr `$ext_projectname$`, który jest kopią `$projectname$`parametr z nadrzędnym szablonie grupowym.<br /><br /> Dzięki temu połączone szablony mogą korzystać z niektórych wspólnych parametrów tworzonych wygodnie tylko w nadrzędnym szablonie grupowym.<br /><br /> Ten atrybut jest opcjonalny, a następnie automatycznie wartość domyślna to `false` gdy nie jest dołączony.<br /><br /> Wprowadzona w programie Visual Studio 2013 Update 2. Aby odwoływać się do wersji produktu jest poprawny, zobacz [odwołuje się do zestawów dostarczane w Visual Studio 2013 SDK Update 2](https://msdn.microsoft.com/library/42b65c3e-e42b-4c39-98c8-bea285f25ffb).|

### <a name="child-elements"></a>Elementy podrzędne
 Brak.

### <a name="parent-elements"></a>Elementy nadrzędne

|Element|Opis|
|-------------|-----------------|
|[ProjectCollection](../extensibility/projectcollection-element-visual-studio-templates.md)|Określa organizację i zawartość szablonów wieloprojektowych.|
|[SolutionFolder](../extensibility/solutionfolder-element-visual-studio-templates.md)|Grupowanie projektów w szablonach wieloprojektowych.|

## <a name="text-value"></a>Wartość tekstowa
 Wartość tekstowa jest wymagana.

 Ten tekst Określa ścieżkę do *.vstemplate* pliku szablonu.

## <a name="remarks"></a>Uwagi
 Szablony wieloprojektowe działają jak kontenery dla dwóch lub więcej projektów. `ProjectTemplateLink` Element jest używany do określenia lokalizacji *.vstemplate* pliku dla jednego z projektów w szablonie. *.Vstemplate* plik szablonu wieloprojektowego zawiera jeden `ProjectTemplateLink` elementu dla każdego projektu w szablonie. Aby uzyskać więcej informacji o szablonach wieloprojektowych, zobacz [jak: Tworzenie szablonów wielu projektów](../ide/how-to-create-multi-project-templates.md).

## <a name="example"></a>Przykład
 W tym przykładzie pokazano prosty główny wielu projektów *.vstemplate* pliku. W tym przykładzie szablon zawiera dwa projekty `My Windows Application` i `My Class Library`. `ProjectName` Atrybutu na `ProjectTemplateLink` element ustawia nazwę [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] przypisze temu projektowi. Jeśli `ProjectName` nie istnieje atrybut nazwy *.vstemplate* plik jest używany jako nazwa projektu.

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

## <a name="see-also"></a>Zobacz także
- [Odwołanie do schematu szablonu Visual Studio](../extensibility/visual-studio-template-schema-reference.md)
- [Tworzenie szablonów projektów i elementów](../ide/creating-project-and-item-templates.md)
- [Instrukcje: Tworzenie szablonów wielu projektów](../ide/how-to-create-multi-project-templates.md)