---
title: VSTemplate — Element (szablony Visual Studio) | Dokumentacja firmy Microsoft
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
- http://schemas.microsoft.com/developer/vstemplate/2005#VSTemplate
helpviewer_keywords:
- VSTemplate element [Visual Studio project templates]
ms.assetid: f8ac561b-3b0b-4246-9ec9-118d2447e9a9
caps.latest.revision: 21
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: c497d264e9bf8b4f62559d9c4cfbb4fdb45cd7e4
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/16/2018
ms.locfileid: "51758015"
---
# <a name="vstemplate-element-visual-studio-templates"></a>VSTemplate — Element (szablony projektów Visual Studio)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Zawiera wszystkie metadane dotyczące szablonu projektu, szablon elementu lub starter kit.  
  
## <a name="syntax"></a>Składnia  
  
```  
<VSTemplate Type="TemplateType" Version="x.x.x">  
    <TemplateData>    </TemplateData>  
    <TemplateContent>    </TemplateContent>  
    ...  
</VSTemplate>  
```  
  
## <a name="attributes-and-elements"></a>Atrybuty i elementy  
 W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.  
  
### <a name="attributes"></a>Atrybuty  
  
|Atrybut|Opis|  
|---------------|-----------------|  
|`Type`|Określa szablon jako szablon projektu lub szablon elementu. Ten atrybut może mieć wartość `Project` lub `Item`.|  
|`Version`|Określa numer wersji dla szablonu. Szablony w [!INCLUDE[vs_dev10_long](../includes/vs-dev10-long-md.md)] i [!INCLUDE[vs_dev11_long](../includes/vs-dev11-long-md.md)] mają `Version` wartość atrybutu `3.0.0`.|  
  
### <a name="child-elements"></a>Elementy podrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[TemplateData](../extensibility/templatedata-element-visual-studio-templates.md)|Element wymagany.<br /><br /> Określa dane, która klasyfikuje szablon i definiuje sposób wyświetlania w **nowy projekt** lub **Dodaj nowy element** okno dialogowe.|  
|[TemplateContent](../extensibility/templatecontent-element-visual-studio-templates.md)|Element wymagany.<br /><br /> Określa zawartość szablonu.|  
|[Wizardextension —](../extensibility/wizardextension-element-visual-studio-templates.md)|Element opcjonalny.|  
|[WizardData](../extensibility/wizarddata-element-visual-studio-templates.md)|Element opcjonalny.|  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
 Brak.  
  
## <a name="remarks"></a>Uwagi  
 `VSTemplate` Element jest elementem głównym pliku .vstemplate.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie pokazano metadanych szablon projektu służący do [!INCLUDE[csprcs](../includes/csprcs-md.md)] aplikacji.  
  
```  
<VSTemplate Type="Project" Version="3.0.0"  
    xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">  
    <TemplateData>  
        <Name>My template</Name>  
        <Description>A basic starter kit</Description>  
        <Icon>TemplateIcon.ico</Icon>  
        <ProjectType>CSharp</ProjectType>  
    </TemplateData>  
    <TemplateContent>  
        <Project File="MyStarterKit.csproj">  
            <ProjectItem>Form1.cs</ProjectItem>  
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

