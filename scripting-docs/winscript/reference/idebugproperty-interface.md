---
title: Interfejs IDebugProperty | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 01/18/2017
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
ms.openlocfilehash: 963b11a4760fad8086822f13db129fae76467802
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2019
ms.locfileid: "58145762"
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