---
title: Interfejs IEnumDebugExtendedPropertyInfo | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IEnumDebugExtendedPropertyInfo
apilocation:
- scrobj.dll
helpviewer_keywords:
- IEnumDebugExtendedPropertyInfo interface
ms.assetid: 316d5aa7-c949-48fc-89c1-239f00566cae
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 2440daf99d9dbb69713d1895ffbfaa18965480a4
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62963484"
---
# <a name="ienumdebugextendedpropertyinfo-interface"></a>Interfejs IEnumDebugExtendedPropertyInfo
Wylicza `ExtendedDebugPropertyInfo` struktury.  
  
## <a name="methods-in-vtable-order"></a>Metody w Vtable kolejności  
 W poniższej tabeli przedstawiono metody `IEnumDebugExtendedPropertyInfo`.  
  
|Metoda|Opis|  
|------------|-----------------|  
|[IEnumDebugExtendedPropertyInfo::Clone](../../winscript/reference/ienumdebugextendedpropertyinfo-clone.md)|Tworzy moduł wyliczający, który zawiera ten sam stan wyliczenia jako bieżącego modułu wyliczającego.|  
|[IEnumDebugExtendedPropertyInfo::GetCount](../../winscript/reference/ienumdebugextendedpropertyinfo-getcount.md)|Pobiera liczbę `ExtendedDebugPropertyInfo` struktury w moduł wyliczający.|  
|[IEnumDebugExtendedPropertyInfo::Next](../../winscript/reference/ienumdebugextendedpropertyinfo-next.md)|Pobiera określoną liczbę `ExtendedDebugPropertyInfo` struktur w kolejności wyliczenia.|  
|[IEnumDebugExtendedPropertyInfo::Skip](../../winscript/reference/ienumdebugextendedpropertyinfo-skip.md)|Pomija określoną liczbę `ExtendedDebugPropertyInfo` struktur w kolejności wyliczenia.|  
|[IEnumDebugExtendedPropertyInfo::Reset](../../winscript/reference/ienumdebugextendedpropertyinfo-reset.md)|Resetuje sekwencji wyliczenia na początku.|  
  
## <a name="requirements"></a>Wymagania  
 Nagłówek: dbgprop.h  
  
## <a name="see-also"></a>Zobacz też  
 [ExtendedDebugPropertyInfo, struktura](../../winscript/reference/extendeddebugpropertyinfo-structure.md)