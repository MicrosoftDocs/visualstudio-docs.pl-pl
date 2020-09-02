---
title: RequiredPlatformVersion, element (szablony Visual Studio) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
ms.assetid: 6f0e4986-3157-4bba-aed3-c28413ebe976
caps.latest.revision: 7
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 2e5ba8cfef6674b5603cf03c73619f686338af3c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "68159289"
---
# <a name="requiredplatformversion-element-visual-studio-templates"></a>RequiredPlatformVersion, element (szablony Visual Studio)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Określa minimalną wersję systemu operacyjnego wymaganą przez szablon projektu do poprawnego działania. Ten element jest używany do szablonów projektów tworzących [!INCLUDE[win8_appname_long](../includes/win8-appname-long-md.md)] aplikacje.  
  
 `RequiredPlatformVersion`Wartość jest porównywana bezpośrednio z wersją systemu operacyjnego. Jeśli `RequiredPlatformVersion` jest wyższa niż wersja systemu operacyjnego, szablon nie jest wyświetlany w oknie dialogowym **Nowy projekt** . Aby określić szablon dla [!INCLUDE[win8](../includes/win8-md.md)] lub wyższy, ustaw wartość `RequiredPlatformVersion` 6.2.0. Aby określić szablon dla [!INCLUDE[win81](../includes/win81-md.md)] lub wyższej, ustaw RequiredPlatformVersion na 6.3.0.  
  
 Szablony określające wartość `RequiredPlatformVersion` = 8 są zgodne z poprzednimi [!INCLUDE[win8_appname_long](../includes/win8-appname-long-md.md)] szablonami klientów.  
  
 VSTemplate  
TemplateData  
..... TargetPlatformName  
RequiredPlatformVersion  
  
## <a name="syntax"></a>Składnia  
  
```xml  
<RequiredPlatformVersion> OperatingSystem </RequiredPlatformVersion>  
```  
  
## <a name="attributes-and-elements"></a>Atrybuty i elementy  
 Brak.  
  
### <a name="attributes"></a>Atrybuty  
 Brak.  
  
### <a name="child-elements"></a>Elementy podrzędne  
 Brak.  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[TemplatePlatformName](../extensibility/templatedata-element-visual-studio-templates.md)|Określa platformę, do której należy szablon projektu.|  
  
## <a name="text-value"></a>Wartość tekstowa  
 Wartość tekstowa jest wymagana.  
  
## <a name="remarks"></a>Uwagi  
 Ten tekst Określa minimalną wersję systemu operacyjnego wymaganą przez szablon.  
  
## <a name="example"></a>Przykład  
 Ten przykład określa, że szablon projektu jest obiektem docelowym [!INCLUDE[win8](../includes/win8-md.md)] lub nowszym.  
  
```xml  
<VSTemplate Type="Project" Version="3.0.0"    xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">  
    <TemplateData>  
        <TargetPlatformName>Windows</TargetPlatformName>  
            <RequiredPlatformVersion>6.3.0</RequiredPlatformVersion>  
  
    </TemplateData>  
    <TemplateContent>  
  
    </TemplateContent>  
</VSTemplate>  
```  
  
## <a name="see-also"></a>Zobacz też  
 [TargetPlatformName, element (szablony Visual Studio)](../extensibility/targetplatformname-element-visual-studio-templates.md)   
 [Tworzenie szablonów projektów i elementów](../ide/creating-project-and-item-templates.md)   
 [Odwołanie do schematu szablonu Visual Studio](../extensibility/visual-studio-template-schema-reference.md)
