---
title: SCRIPT_ERROR_DEBUG_EXCEPTION_THROWN_KIND, Wyliczenie | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: b3aa4966-e110-4b30-b368-1281a9740dbd
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 8eb089efbf608b488465809f997ffc82fc2c2e3c
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2019
ms.locfileid: "72574407"
---
# <a name="script_error_debug_exception_thrown_kind-enumeration"></a>Wyliczenie SCRIPT_ERROR_DEBUG_EXCEPTION_THROWN_KIND
Wskazuje rodzaj zgłaszanego wyjątku. To wyliczenie jest używane przez metodę [IActiveScriptErrorDebug110:: GetExceptionThrownKind](../../winscript/reference/iactivescripterrordebug110-getexceptionthrownkind.md) .  
  
> [!IMPORTANT]
> Te stałe są implementowane przez program PDM w wersji 11.0 i nowszych. Znajduje się w zestawie activdbg100.h.  
  
## <a name="syntax"></a>Składnia  
  
```cpp
typedef SCRIPT_ERROR_DEBUG_EXCEPTION_THROWN_KIND  
```  
  
## <a name="members"></a>Elementy członkowskie  
  
|Element członkowski|Wartość|Opis|  
|------------|-----------|-----------------|  
|ETK_FIRST_CHANCE|0x00000000|Jest to wyjątek pierwszego rzędu.|  
|ETK_USER_UNHANDLED|0x00000001|Wyjątek nie jest obsługiwany w kodzie użytkownika.|  
|ETK_UNHANDLED|0x00000002|Wyjątek nie jest obsługiwany w kodzie.|  
  
## <a name="see-also"></a>Zobacz także  
 [IActiveScriptErrorDebug110, interfejs](../../winscript/reference/iactivescripterrordebug110-interface.md)