---
title: PromptForSaveOnCreation —, element (szablony Visual Studio) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#PromptForSaveOnCreation
helpviewer_keywords:
- PromptForSaveOnCreation element [Visual Studio project templates]
ms.assetid: 75174674-0c3c-4b57-b2fd-6ea8e817b67d
caps.latest.revision: 19
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: a523190a9e5c143667355c222e0fbe9441cc231a
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "65675369"
---
# <a name="promptforsaveoncreation-element-visual-studio-templates"></a>PromptForSaveOnCreation — Element (szablony Visual Studio)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Określa, czy użytkownik jest monitowany o lokalizację zapisywania projektu za pośrednictwem okna dialogowego **Nowy projekt** podczas tworzenia projektu. Jeśli ten element jest ustawiony na `true` , użytkownik jest monitowany o lokalizację zapisu. Jeśli `false` , wówczas nie zostanie wyświetlony monit. (Oznacza to, że tworzony jest projekt tymczasowy).  
  
 \<VSTemplate>  
 \<TemplateData>  
 \<PromptForSaveOnCreation>  
  
## <a name="syntax"></a>Składnia  
  
```  
<PromptForSaveOnCreation> true/false </PromptForSaveOnCreation>  
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
|[TemplateData](../extensibility/templatedata-element-visual-studio-templates.md)|Element wymagany.<br /><br /> Klasyfikuje szablon i definiuje sposób wyświetlania w oknie dialogowym **Nowy projekt** lub **Dodaj nowy element** .|  
  
## <a name="text-value"></a>Wartość tekstowa  
 Wartość tekstowa jest wymagana.  
  
 Tekst musi być albo `true` `false` , `true` co oznacza, że użytkownik będzie monitowany o lokalizację zapisu podczas tworzenia nowego projektu.  
  
## <a name="remarks"></a>Uwagi  
 `PromptForSaveOnCreation` jest elementem opcjonalnym. Wartość domyślna to `false`.  
  
 Projekty tymczasowe to projekty, które można tworzyć i modyfikować bez zapisywania zawartości tego projektu na dysku. Aby uzyskać więcej informacji, zobacz [NIB Temporary projects](https://msdn.microsoft.com/9cf1944c-7045-44cc-8701-7b0eb4099f2b).  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie ustawiono wartość `PromptForSaveOnCreation` równą `false` , która określa, że projekt ma być tworzony jako projekt tymczasowy.  
  
```  
<VSTemplate Type="Project" Version="3.0.0"  
    xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">  
    <TemplateData>  
        <Name>My template</Name>  
        <Description>A basic template</Description>  
        <Icon>TemplateIcon.ico</Icon>  
        <ProjectType>CSharp</ProjectType>  
        <PromptForSaveOnCreation>false</PromptForSaveOnCreation>  
    </TemplateData>  
    <TemplateContent>  
        <Project File="MyTemplate.csproj">  
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
 [Odwołanie do schematu szablonu programu Visual Studio](../extensibility/visual-studio-template-schema-reference.md)   
 [Tworzenie szablonów projektu i elementu](../ide/creating-project-and-item-templates.md)
