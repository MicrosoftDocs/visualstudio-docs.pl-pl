---
title: Interfejs IEnumDebugPropertyInfo | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IEnumDebugPropertyInfo interface
ms.assetid: c5eea4da-8414-408a-a8f6-6a9ca8745868
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 0ce4f5a114629a473df99b583c77ae7747bcd339
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2019
ms.locfileid: "72574188"
---
# <a name="ienumdebugpropertyinfo-interface"></a>Interfejs IEnumDebugPropertyInfo
Wylicza struktury `DebugPropertyInfo`.  
  
## <a name="methods-in-vtable-order"></a>Metody w kolejności tablic wirtualnych  
 W poniższej tabeli przedstawiono metody `IEnumDebugPropertyInfo`.  
  
|Metoda|Opis|  
|------------|-----------------|  
|[IEnumDebugPropertyInfo::Next](../../winscript/reference/ienumdebugpropertyinfo-next.md)|Pobiera określoną liczbę struktur `DebugPropertyInfo` w sekwencji wyliczenia.|  
|[IEnumDebugPropertyInfo::Skip](../../winscript/reference/ienumdebugpropertyinfo-skip.md)|Pomija określoną liczbę struktur `DebugPropertyInfo` w sekwencji wyliczenia.|  
|[IEnumDebugPropertyInfo::Reset](../../winscript/reference/ienumdebugpropertyinfo-reset.md)|Resetuje sekwencję wyliczenia na początek.|  
|[IEnumDebugPropertyInfo::Clone](../../winscript/reference/ienumdebugpropertyinfo-clone.md)|Tworzy moduł wyliczający, który zawiera ten sam stan wyliczania co bieżący moduł wyliczający.|  
|[IEnumDebugPropertyInfo::GetCount](../../winscript/reference/ienumdebugpropertyinfo-getcount.md)|Pobiera liczbę struktur `DebugPropertyInfo` w module wyliczającym.|  
  
## <a name="requirements"></a>Wymagania  
 Nagłówek: dbgprop. h  
  
## <a name="see-also"></a>Zobacz także  
 [DebugPropertyInfo, struktura](../../winscript/reference/debugpropertyinfo-structure.md)