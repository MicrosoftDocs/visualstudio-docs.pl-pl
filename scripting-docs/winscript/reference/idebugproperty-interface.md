---
title: Interfejs IDebugProperty | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IDebugProperty interface
ms.assetid: 7e8f5341-23ef-4029-814d-f5c2307b9203
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 2e5e5274e8a3d1c81ce010afc3893b27510a0fad
ms.sourcegitcommit: 8bf9e51c77a5a602fab9513b9187e59e57dfebad
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/16/2019
ms.locfileid: "54348363"
---
# <a name="idebugproperty-interface"></a>Interfejs IDebugProperty
Używany do opisania hierarchiczne właściwości obiektu debugowanego, który ma nazwę, typ i wartość. Najczęściej `IDebugProperty` służy do opisywania wynikiem obliczenia wyrażenia, oceny instrukcji lub zarejestruj oceny.  
  
## <a name="methods-in-vtable-order"></a>Metody w Vtable kolejności  
 W poniższej tabeli przedstawiono metody `IDebugProperty` interfejsu.  
  
|Metoda|Opis|  
|------------|-----------------|  
|[IDebugProperty::GetPropertyInfo](../../winscript/reference/idebugproperty-getpropertyinfo.md)|Pobierz `DebugPropertyInfo` , który opisuje to `IDebugProperty``.`|  
|[IDebugProperty::GetExtendedInfo](../../winscript/reference/idebugproperty-getextendedinfo.md)|Pobiera rozszerzone informacje o właściwości.|  
|[IDebugProperty::SetValueAsString](../../winscript/reference/idebugproperty-setvalueasstring.md)|Ustawia wartości właściwości z ciągu.|  
|[IDebugProperty::EnumMembers](../../winscript/reference/idebugproperty-enummembers.md)|Wylicza właściwości elementów członkowskich.|  
|[IDebugProperty::GetParent](../../winscript/reference/idebugproperty-getparent.md)|Pobiera element nadrzędny właściwości.|  
  
## <a name="requirements"></a>Wymagania  
 Nagłówek: dbgprop.h