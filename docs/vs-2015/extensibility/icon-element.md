---
title: Ikona — element | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
helpviewer_keywords:
- VSCT XML schema elements, Icon
- Icon element (VSCT XML schema)
ms.assetid: 73c58fe3-d53c-4f4e-b025-29567c6cbb7c
caps.latest.revision: 6
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: ca5ced87596b5e40ae70e3faa06e58493da3d8ab
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "68203992"
---
# <a name="icon-element"></a>Icon, element
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Atrybut GUID tagu Icon jest identyfikatorem GUID zdefiniowanej mapy bitowej.  Atrybut ID wybiera miejsce na pasku mapy bitowej. Ten element jest opcjonalny.  Jeśli ten element zostanie pominięty, wartość **guidOfficeIcon: msotcidNoIcon** zostanie implikowana.  
  
## <a name="syntax"></a>Składnia  
  
```  
<Icon guid="guidImages" id="bmpPic1" />  
```  
  
## <a name="attributes-and-elements"></a>Atrybuty i elementy  
 W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.  
  
### <a name="attributes"></a>Atrybuty  
  
|Atrybut|Opis|  
|---------------|-----------------|  
|guid|Wymagany. Identyfikator GUID zdefiniowanej mapy bitowej.|  
|identyfikator|Wymagany. Wybiera miejsce na pasku mapy bitowej.|  
  
### <a name="child-elements"></a>Elementy podrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|Brak.|Brak.|  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[Buttons, element](../extensibility/buttons-element.md)||  
  
## <a name="see-also"></a>Zobacz też  
 [Tabela poleceń programu Visual Studio (pliki Vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
