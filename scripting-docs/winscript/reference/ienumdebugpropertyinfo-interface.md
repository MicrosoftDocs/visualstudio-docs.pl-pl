---
title: Interfejs IEnumDebugPropertyInfo | Dokumentacja firmy Microsoft
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
ms.openlocfilehash: 736bea847908e3c70d6caf2f8e41af38608f4f23
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2019
ms.locfileid: "58157571"
---
# <a name="ienumdebugpropertyinfo-interface"></a>Interfejs IEnumDebugPropertyInfo
Wylicza `DebugPropertyInfo` struktury.  
  
## <a name="methods-in-vtable-order"></a>Metody w Vtable kolejności  
 W poniższej tabeli przedstawiono metody `IEnumDebugPropertyInfo`.  
  
|Metoda|Opis|  
|------------|-----------------|  
|[IEnumDebugPropertyInfo::Next](../../winscript/reference/ienumdebugpropertyinfo-next.md)|Pobiera określoną liczbę `DebugPropertyInfo` struktur w kolejności wyliczenia.|  
|[IEnumDebugPropertyInfo::Skip](../../winscript/reference/ienumdebugpropertyinfo-skip.md)|Pomija określoną liczbę `DebugPropertyInfo` struktur w kolejności wyliczenia.|  
|[IEnumDebugPropertyInfo::Reset](../../winscript/reference/ienumdebugpropertyinfo-reset.md)|Resetuje sekwencji wyliczenia na początku.|  
|[IEnumDebugPropertyInfo::Clone](../../winscript/reference/ienumdebugpropertyinfo-clone.md)|Tworzy moduł wyliczający, który zawiera ten sam stan wyliczenia jako bieżącego modułu wyliczającego.|  
|[IEnumDebugPropertyInfo::GetCount](../../winscript/reference/ienumdebugpropertyinfo-getcount.md)|Pobiera liczbę `DebugPropertyInfo` struktury w moduł wyliczający.|  
  
## <a name="requirements"></a>Wymagania  
 Nagłówek: dbgprop.h  
  
## <a name="see-also"></a>Zobacz też  
 [DebugPropertyInfo, struktura](../../winscript/reference/debugpropertyinfo-structure.md)