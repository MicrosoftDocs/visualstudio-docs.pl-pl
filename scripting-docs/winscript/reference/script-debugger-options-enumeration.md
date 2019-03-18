---
title: Wyliczenie SCRIPT_DEBUGGER_OPTIONS | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- SCRIPT_DEBUGGER_OPTIONS Enumeration
ms.assetid: aef41ec0-6f65-48e8-a69e-44b4e4fb929f
caps.latest.revision: 5
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 25f74902e2fea451ae5ddaf75d215c3a6c70b050
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2019
ms.locfileid: "58155046"
---
# <a name="scriptdebuggeroptions-enumeration"></a>Wyliczenie SCRIPT_DEBUGGER_OPTIONS
Wskazuje zestaw opcji i/lub funkcje, które są stosowane do dołączonego debugera. Używane w [IDebugApplicationNode100::GetExcludedDocuments](../../winscript/reference/idebugapplicationnode100-getexcludeddocuments.md) i [IDebugApplicationNode100::SetFilterForEventSink](../../winscript/reference/idebugapplicationnode100-setfilterforeventsink.md)  
  
> [!IMPORTANT]
>  Te stałe są implementowane przez program PDM 10.0 lub nowszym. Znajduje się w zestawie activdbg100.h.  
  
## <a name="syntax"></a>Składnia  
  
```cpp
typedef SCRIPT_DEBUGGER_OPTIONS  
```  
  
## <a name="members"></a>Elementy członkowskie  
  
|Element członkowski|Wartość|Opis|  
|------------|-----------|-----------------|  
|SDO_NONE|0x00000000|Brak opcji są ustawione.|  
|SDO_ENABLE_FIRST_CHANCE_EXCEPTIONS|0x00000001|Wskazuje, że wykonywania skryptów, powinny wywoływać zdarzenia BREAKREASON_ERROR, gdy wyjątek jest zgłaszany. Ta opcja może być ustawione przez debuger lub ustawiony przez kod użytkownika za pośrednictwem `Debug.enableFirstChanceExceptions(<true&#124;false>)`.|  
|SDO_ENABLE_WEB_WORKER_SUPPORT|0x00000002|Wskazuje, że dołączony debuger obsługuje internetowych procesów roboczych.|  
  
## <a name="see-also"></a>Zobacz też  
 [Stałe, wyliczenia i struktury debugera aktywnego skryptu](../../winscript/reference/active-script-debugger-constants-enumerations-and-structures.md)