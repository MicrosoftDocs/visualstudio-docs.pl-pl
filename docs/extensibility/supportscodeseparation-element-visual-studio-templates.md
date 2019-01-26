---
title: Supportscodeseparation — Element (szablony Visual Studio) | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#SupportsCodeSeparation
helpviewer_keywords:
- SupportsCodeSeparation element [Visual Studio Templates]
- <SupportsCodeSeparation> element [Visual Studio Templates]
ms.assetid: 8112aac8-a269-40e5-b92b-9b9a6ff5a542
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 9d054348ea88fda4e6e6f7102aaddf49acfe1100
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/26/2019
ms.locfileid: "55070477"
---
# <a name="supportscodeseparation-element-visual-studio-templates"></a>SupportsCodeSeparation — Element (szablony Visual Studio)
Określa, czy **umieść kod w oddzielnym pliku** pole wyboru jest włączone w **Dodaj nowy element** okno dialogowe.  
  
 \<VSTemplate>  
 \<TemplateData>  
 \<SupportsCodeSeparation>  
  
## <a name="syntax"></a>Składnia  
  
```  
<SupportsCodeSeparation> true/false </SupportsCodeSeparation>  
```  
  
## <a name="attributes-and-elements"></a>Atrybuty i elementy  
 W poniższych sekcjach opisano atrybut, elementy podrzędne i elementy nadrzędne.  
  
### <a name="attributes"></a>Atrybuty  
 Brak.  
  
### <a name="child-elements"></a>Elementy podrzędne  
 Brak.  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[TemplateData](../extensibility/templatedata-element-visual-studio-templates.md)|Element wymagany.<br /><br /> Klasyfikuje szablon i definiuje sposób wyświetlania albo **nowy projekt** lub **nowy element** okno dialogowe.|  
  
## <a name="text-value"></a>Wartość tekstowa  
 Wartość tekstowa jest wymagana.  
  
 Tekst musi być albo `true` lub `false`oznaczający czy **umieść kod w oddzielnym pliku** pole wyboru jest włączone w **Dodaj nowy element** okno dialogowe.  
  
## <a name="remarks"></a>Uwagi  
 `SupportsCodeSeparation` element jest opcjonalny. Wartość domyślna to `false`.  
  
 `SupportsCodeSeparation` Element jest dostępny tylko dla szablonów elementów sieci Web.  
  
 Separacja kodu lub modelu strony związanym z kodem, pozwala na zachowanie znaczników w jednym pliku i programowania kod w innym pliku. [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] i innymi językami .NET użyć tego modelu.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład określa, aby wyświetlić **umieść kod w oddzielnym pliku** opcji.  
  
```  
<VSTemplate Version="3.0.0" Type="Project"  
    xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">>  
    <TemplateData>  
        <Name>MyWebProjecStarterKit</Name>  
        <Description>A simple Web template</Description>  
        <Icon>icon.ico</Icon>  
        <ProjectType>Web</ProjectType>  
        <ProjectSubType>CSharp</ProjectSubType>  
        <DefaultName>WebSite</DefaultName>  
        <SupportsCodeSeparation>true</SupportsCodeSeparation>  
    </TemplateData>  
    <TemplateContent>  
        <Project File="WebApplication.webproj">  
            <ProjectItem>icon.ico</ProjectItem>  
            <ProjectItem OpenInEditor="true">Default.aspx</ProjectItem>  
            <ProjectItem>Default.aspx.cs</ProjectItem>  
        </Project>  
    </TemplateContent>  
</VSTemplate>  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Visual Studio Template Schema Reference](../extensibility/visual-studio-template-schema-reference.md)   
 [Tworzenie szablonów projektu i elementu](../ide/creating-project-and-item-templates.md)