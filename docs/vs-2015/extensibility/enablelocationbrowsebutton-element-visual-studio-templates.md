---
title: EnableLocationBrowseButton, Element (szablony Visual Studio) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#EnableLocationBrowseButton
helpviewer_keywords:
- EnableLocationBrowseButton [Visual Studio project templates]
ms.assetid: a12d10d8-af49-482a-af77-e084fd07a47d
caps.latest.revision: 12
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 04d5710012840079e3381f09725b96b8f329872d
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/16/2018
ms.locfileid: "51795742"
---
# <a name="enablelocationbrowsebutton-element-visual-studio-templates"></a>EnableLocationBrowseButton — Element (szablony Visual Studio)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Określa, czy **Przeglądaj** przycisk jest dostępny w **nowy projekt** okno dialogowe, dzięki czemu użytkownicy mogą łatwo modyfikować domyślny katalog, w której zostanie zapisany nowy projekt.  
  
 \<VSTemplate>  
 \<TemplateData >  
 \<EnableLocationBrowseButton >  
  
## <a name="syntax"></a>Składnia  
  
```  
<EnableLocationBrowseButton> true/false </EnableLocationBrowseButton>  
```  
  
## <a name="attributes-and-elements"></a>Atrybuty i elementy  
 W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.  
  
### <a name="attributes"></a>Atrybuty  
 Brak.  
  
### <a name="child-elements"></a>Elementy podrzędne  
 Brak.  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[TemplateData](../extensibility/templatedata-element-visual-studio-templates.md)|Element wymagany.<br /><br /> Klasyfikuje szablon i definiuje sposób wyświetlania albo **nowy projekt** lub **Dodaj nowy element** okno dialogowe.|  
  
## <a name="text-value"></a>Wartość tekstowa  
 Wartość tekstowa jest wymagana.  
  
 Tekst musi być albo `true` lub `false`, wskazującą, czy mają być wyświetlane **Przeglądaj** znajdujący się na **nowy projekt** okno dialogowe.  
  
## <a name="remarks"></a>Uwagi  
 `EnableLocationBrowseButton` element jest opcjonalny. Wartość domyślna to `true`, który wyświetla **Przeglądaj** znajdujący się w **nowy projekt** okno dialogowe.  
  
 W **nowy projekt** okno dialogowe **lokalizacji** pola tekstowego określa katalog, w której zostanie zapisany nowy projekt. **Przeglądaj** przycisk pomoże Ci modyfikować tego katalogu, wyświetlając **lokalizacji projektu** okno dialogowe, które umożliwia łatwe przejście do innego katalogu, który jest dostępny z komputera, a następnie wybierz ją, jako katalog, w którym jest zapisywany nowy projekt.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie pokazano metadanych [!INCLUDE[csprcs](../includes/csprcs-md.md)] aplikacji Windows.  
  
```  
<VSTemplate Type="Project" Version="3.0.0"  
    xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">  
    <TemplateData>  
        <Name>My template</Name>  
        <Description>A basic starter kit</Description>  
        <Icon>TemplateIcon.ico</Icon>  
        <ProjectType>CSharp</ProjectType>  
        <EnableLocationBrowseButton>false</EnableLocationBrowseButton>  
    </TemplateData>  
    <TemplateContent>  
        <Project File="MyStarterKit.csproj">  
            <ProjectItem>Form1.cs<ProjectItem>  
            <ProjectItem>Form1.Designer.cs</ProjectItem>  
            <ProjectItem>Program.cs</ProjectItem>  
            <ProjectItem>Properties\AssemblyInfo.cs</ProjectItem>  
            <ProjectItem>Properties\Resources.resx</ProjectItem>  
            <ProjectItem>Properties\Resources.Designer.cs</ProjectItem>  
            <ProjectItem>Properties\Settings.settings</ProjectItem>  
            <ProjectItem>Properties\Settings.Designer.cs</ProjectItem>  
        </Project>  
    </TemplateContent>  
</VSTemplate>  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Odwołanie do schematu szablonu Visual Studio](../extensibility/visual-studio-template-schema-reference.md)   
 [Tworzenie szablonów projektu i elementu](../ide/creating-project-and-item-templates.md)

