---
title: Interfejs IScriptScriptlet | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IScriptScriptlet interface
ms.assetid: b9981908-a337-4228-864c-c741f111ab2d
caps.latest.revision: 11
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: a3b7c4af7769a1a2851e9be4e2639a324a3c06fb
ms.sourcegitcommit: 8bf9e51c77a5a602fab9513b9187e59e57dfebad
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/16/2019
ms.locfileid: "54345919"
---
# <a name="iscriptscriptlet-interface"></a>Interfejs IScriptScriptlet
Obiekt, który implementuje `IScriptScriptlet` interfejs reprezentuje skrypt procedury obsługi zdarzeń.  
  
 Oprócz metod odziedziczone `IScriptEntry`, `IScriptScriptlet` interfejsu udostępnia następujące metody.  
  
## <a name="methods-in-vtable-order"></a>Metody w Vtable kolejności  
  
|Metoda|Opis|  
|------------|-----------------|  
|[IScriptScriptlet::GetEventName](../../winscript/reference/iscriptscriptlet-geteventname.md)|Zwraca nazwę zdarzenia, które jest skojarzone ze scriptlet.|  
|[IScriptScriptlet:: GetSimpleEventName](../../winscript/reference/iscriptscriptlet-getsimpleeventname.md)|Zwraca nazwę zdarzenia prostego, który jest skojarzony z scriptlet. Jest to nazwa jednowyrazowej, który nie zawiera żadnego odstępu.|  
|[IScriptScriptlet::GetSubItemName](../../winscript/reference/iscriptscriptlet-getsubitemname.md)|Zwraca ostatni identyfikator w pełni kwalifikowaną nazwę hosta obiektu scriptlet.|  
|[IScriptScriptlet::SetEventName](../../winscript/reference/iscriptscriptlet-seteventname.md)|Ustawia nazwę zdarzenia, które jest skojarzone ze scriptlet.|  
|[IScriptScriptlet::SetSimpleEventName](../../winscript/reference/iscriptscriptlet-setsimpleeventname.md)|Ustawia nazwę zdarzenia prostego, który jest skojarzony z scriptlet. Jest to nazwa jednowyrazowej, który nie zawiera żadnego odstępu.|  
|[IScriptScriptlet::SetSubItemName](../../winscript/reference/iscriptscriptlet-setsubitemname.md)|Ustawia identyfikator ostatniego w pełni kwalifikowaną nazwę hosta obiektu scriptlet.|  
  
## <a name="see-also"></a>Zobacz też  
 [Interfejsy tworzenia aktywnych skryptów](../../winscript/reference/active-script-authoring-interfaces.md)