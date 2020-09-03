---
title: EnableLocationBrowseButton, element (szablony Visual Studio) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#EnableLocationBrowseButton
helpviewer_keywords:
- EnableLocationBrowseButton [Visual Studio project templates]
ms.assetid: a12d10d8-af49-482a-af77-e084fd07a47d
caps.latest.revision: 12
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: ef9f42bfb24caaf2775ba2c70110eaaa5d616116
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "68204594"
---
# <a name="enablelocationbrowsebutton-element-visual-studio-templates"></a>EnableLocationBrowseButton — Element (szablony Visual Studio)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Określa, czy przycisk **Przeglądaj** jest dostępny w oknie dialogowym **Nowy projekt** , dzięki czemu użytkownicy mogą łatwo modyfikować domyślny katalog, w którym zapisano nowy projekt.  
  
 \<VSTemplate>  
 \<TemplateData>  
 \<EnableLocationBrowseButton>  
  
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
|[TemplateData](../extensibility/templatedata-element-visual-studio-templates.md)|Element wymagany.<br /><br /> Klasyfikuje szablon i definiuje sposób wyświetlania w oknie dialogowym **Nowy projekt** lub **Dodaj nowy element** .|  
  
## <a name="text-value"></a>Wartość tekstowa  
 Wartość tekstowa jest wymagana.  
  
 Tekst musi mieć wartość `true` lub `false` , wskazującą, czy przycisk **Przeglądaj** ma być wyświetlany w oknie dialogowym **Nowy projekt** .  
  
## <a name="remarks"></a>Uwagi  
 `EnableLocationBrowseButton` jest elementem opcjonalnym. Wartość domyślna to `true` , która wyświetla przycisk **Przeglądaj** w oknie dialogowym **Nowy projekt** .  
  
 W oknie dialogowym **Nowy projekt** pole tekstowe **Lokalizacja** określa katalog, w którym jest zapisywany nowy projekt. Przycisk **Przeglądaj** pomaga zmodyfikować ten katalog, wyświetlając okno dialogowe **Lokalizacja projektu** , które pozwala na łatwe przejście do innego katalogu, który jest dostępny na komputerze, a następnie wybranie go jako katalogu, w którym zapisano nowy projekt.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład ilustruje metadane dla [!INCLUDE[csprcs](../includes/csprcs-md.md)] aplikacji systemu Windows.  
  
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
 [Odwołanie do schematu szablonu programu Visual Studio](../extensibility/visual-studio-template-schema-reference.md)   
 [Tworzenie szablonów projektu i elementu](../ide/creating-project-and-item-templates.md)
