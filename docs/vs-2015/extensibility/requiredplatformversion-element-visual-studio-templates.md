---
title: RequiredPlatformVersion, Element (szablony Visual Studio) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 6f0e4986-3157-4bba-aed3-c28413ebe976
caps.latest.revision: 7
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: d2854cd8f10725ed884c27c2c78a4d107054a5bd
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/16/2018
ms.locfileid: "51763976"
---
# <a name="requiredplatformversion-element-visual-studio-templates"></a>RequiredPlatformVersion, element (szablony Visual Studio)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Określa minimalną wersję systemu operacyjnego, który szablon projektu wymaga, aby działać poprawnie. Ten element jest używany do szablonów projektu, tworzonych [!INCLUDE[win8_appname_long](../includes/win8-appname-long-md.md)] aplikacji.  
  
 `RequiredPlatformVersion` Wartość jest porównywana bezpośrednio z wersją systemu operacyjnego. Jeśli `RequiredPlatformVersion` jest wyższa niż wersja systemu operacyjnego nie ma szablonu **nowy projekt** okno dialogowe. Aby określić szablon dla [!INCLUDE[win8](../includes/win8-md.md)] lub nowszej, który jest ustawiony `RequiredPlatformVersion` do 6.2.0. Aby określić szablon dla [!INCLUDE[win81](../includes/win81-md.md)] lub nowszej, który jest ustawiony RequiredPlatformVersion do wersji 6.3.0.  
  
 Szablony, które określają `RequiredPlatformVersion`= 8 są zgodne z poprzedniego klienta [!INCLUDE[win8_appname_long](../includes/win8-appname-long-md.md)] szablonów.  
  
 VSTemplate  
TemplateData  
... TargetPlatformName  
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
|[TemplatePlatformName](../extensibility/templatedata-element-visual-studio-templates.md)|Określa platformę, że projekt jest ukierunkowany szablonu.|  
  
## <a name="text-value"></a>Wartość tekstowa  
 Wartość tekstowa jest wymagana.  
  
## <a name="remarks"></a>Uwagi  
 Ten tekst Określa wersję minimalną wersję systemu operacyjnego wymagane przez szablon.  
  
## <a name="example"></a>Przykład  
 W tym przykładzie określa, że projekt jest ukierunkowany szablonu [!INCLUDE[win8](../includes/win8-md.md)] lub nowszej.  
  
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
 [TargetPlatformName, Element (szablony Visual Studio)](../extensibility/targetplatformname-element-visual-studio-templates.md)   
 [Tworzenie szablonów projektów i elementów](../ide/creating-project-and-item-templates.md)   
 [Odwołanie do schematu szablonu Visual Studio](../extensibility/visual-studio-template-schema-reference.md)

