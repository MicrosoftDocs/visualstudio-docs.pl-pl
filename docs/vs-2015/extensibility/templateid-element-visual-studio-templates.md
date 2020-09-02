---
title: TemplateID, element (szablony Visual Studio) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#TemplateID
helpviewer_keywords:
- <TemplateID> element [Visual Studio Templates]
- TemplateID element [Visual Studio Templates]
ms.assetid: 6ca24b4e-0325-4a9e-855e-0cbbe7361d8f
caps.latest.revision: 16
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: f1a52b360994c53eef69ceafa45828ec1020be16
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "68186423"
---
# <a name="templateid-element-visual-studio-templates"></a>TemplateID — Element (szablony Visual Studio)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Określa identyfikator szablonu elementu, który jest kategoryzowany w grupie szablonów elementów przez element [TemplateGroupID](../extensibility/templategroupid-element-visual-studio-templates.md) .  
  
 \<VSTemplate>  
 \<TemplateData>  
 \<TemplateID>  
  
## <a name="syntax"></a>Składnia  
  
```  
<TemplateID> ... </TemplateID>  
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
 `string`Reprezentuje identyfikator szablonu elementu, który jest kategoryzowany w grupie szablonów elementów według `TemplateGroupID` elementu.  
  
## <a name="remarks"></a>Uwagi  
 `TemplateID` jest elementem opcjonalnym.  
  
 Jeśli plik. vstemplate pomija `TemplateID` element, wówczas element [name](../extensibility/name-element-visual-studio-templates.md) jest używany jako identyfikator szablonu.  
  
 Wartość `TemplateID` elementu jest używana wraz z rejestracją systemu projektu (HKEY_LOCAL_MACHINE \software\microsoft\visualstudio\11.0\Projects \\ ) do filtrowania szablonów, które pojawiają się w oknie dialogowym **Dodaj nowy element** .  
  
## <a name="see-also"></a>Zobacz też  
 [Odwołanie do schematu szablonu programu Visual Studio](../extensibility/visual-studio-template-schema-reference.md)   
 [Tworzenie szablonów projektu i elementu](../ide/creating-project-and-item-templates.md)
