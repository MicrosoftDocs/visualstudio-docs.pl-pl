---
title: Interfejs IDebugExtendedProperty | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IDebugExtendedProperty interface
ms.assetid: e92ea064-0d92-44cf-bb9f-abda783d84be
caps.latest.revision: 10
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: c1e042f75cf0ab0d8c4807c0c0db6ce04e8423f9
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62945877"
---
# <a name="idebugextendedproperty-interface"></a>Interfejs IDebugExtendedProperty
Rozszerza `IDebugProperty` interfejsu.  
  
## <a name="methods-in-vtable-order"></a>Metody w Vtable kolejności  
 Oprócz metod odziedziczone `IDebugProperty`, ten interfejs udostępnia następujące metody.  
  
|Metoda|Opis|  
|------------|-----------------|  
|[IDebugExtendedProperty::GetExtendedPropertyInfo](../../winscript/reference/idebugextendedproperty-getextendedpropertyinfo.md)|Pobiera `ExtendedDebugPropertyInfo` , który opisuje to `IDebugExtendedProperty``.`|  
|[IDebugExtendedProperty::EnumExtendedMembers](../../winscript/reference/idebugextendedproperty-enumextendedmembers.md)|Wylicza członkowie właściwości rozszerzonej.|  
  
## <a name="requirements"></a>Wymagania  
 Nagłówek: dbgprop.h  
  
## <a name="see-also"></a>Zobacz też  
 [IDebugProperty, interfejs](../../winscript/reference/idebugproperty-interface.md)