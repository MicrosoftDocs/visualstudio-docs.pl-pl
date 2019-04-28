---
title: Wyliczenie SCRIPT_ERROR_DEBUG_EXCEPTION_THROWN_KIND | Dokumentacja firmy Microsoft
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
ms.openlocfilehash: 3be6989195eacdd4d70bd13790d55e4f6cfc769d
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "63443646"
---
# <a name="scripterrordebugexceptionthrownkind-enumeration"></a>Wyliczenie SCRIPT_ERROR_DEBUG_EXCEPTION_THROWN_KIND
Wskazuje rodzaj zgłaszanego wyjątku. To wyliczenie jest używane przez [IActiveScriptErrorDebug110::GetExceptionThrownKind](../../winscript/reference/iactivescripterrordebug110-getexceptionthrownkind.md) metody.  
  
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
  
## <a name="see-also"></a>Zobacz też  
 [IActiveScriptErrorDebug110, interfejs](../../winscript/reference/iactivescripterrordebug110-interface.md)