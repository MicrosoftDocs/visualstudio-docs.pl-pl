---
title: Templategroupid — Element (szablony Visual Studio) | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#TemplateGroupID
helpviewer_keywords:
- TemplateGroupID element [Visual Studio Templates]
- <TemplateGroupID> element [Visual Studio Templates]
ms.assetid: bce7b49a-90bc-4691-aff3-a87e209f6d83
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: be9a74c4aedf49b9ff7f7d56c29f3281c2d4578f
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/25/2019
ms.locfileid: "54952811"
---
# <a name="templategroupid-element-visual-studio-templates"></a>TemplateGroupID — Element (szablony Visual Studio)
Określa, jakiego typu Projekt szablonów elementów będą widoczne w. Ten element jest istotne, kiedy [ShowByDefault (szablony Visual Studio)](../extensibility/showbydefault-visual-studio-templates.md) ustawiono `false`. Gdy [ShowByDefault (szablony Visual Studio)](../extensibility/showbydefault-visual-studio-templates.md) jest ustawiona na `true`, a następnie szablon elementu jest dostępny w wszystkich typów projektów.  
  
 \<VSTemplate>  
 \<TemplateData>  
 \<TemplateGroupID>  
  
## <a name="syntax"></a>Składnia  
  
```  
<TemplateGroupID> ... </TemplateGroupID>  
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
|[TemplateData](../extensibility/templatedata-element-visual-studio-templates.md)|Klasyfikuje szablon i definiuje sposób wyświetlania albo **nowy projekt** lub **Dodaj nowy element** okno dialogowe.|  
  
## <a name="text-value"></a>Wartość tekstowa  
 Wartość tekstowa jest wymagana.  
  
 Tekst Określa identyfikator kategorii szablonów elementów.  
  
## <a name="remarks"></a>Uwagi  
 `TemplateGroupID` jest elementem.  
  
 Wartość `TemplateGroupID` element jest używany razem z rejestracji systemu projektu (HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\\*\<numer wersji >* \Projects\\) Filtr szablonów, które pojawiają się w **Dodaj nowy element** okno dialogowe.  
  
|Visual C++ Value|Znaczenie|  
|------------------------|-------------|  
|VC-Native|Używany do natywnych projektów. Również domyślnie, jeśli nie można ustalić typu projektu.|  
|VC-Managed|Używane dla zarządzanych (/ clr) projektów|  
|VC-Windows|Używane dla wszystkich projektów, których platformą docelową będzie system windows (natywnego/zarządzanego/magazyn)|  
|WinRT-Native-UAP|Używane w projektach magazynu systemu Windows 10|  
|CodeSharing-Native|Używane w projektach elementu Shared|  
|WinRT-Native-6.3|Używane w projektach Store Windows 8.1|  
|WinRT-Native-Phone-6.3|Używany do projektów Windows Phone 8.1|  
|WinRT-Native|Używany do projektów Windows 8.0 Store|  
|VC-Android|Używane w projektach systemu Android|  
  
## <a name="see-also"></a>Zobacz też  
 [Visual Studio Template Schema Reference](../extensibility/visual-studio-template-schema-reference.md)   
 [Tworzenie szablonów projektu i elementu](../ide/creating-project-and-item-templates.md)