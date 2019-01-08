---
title: Wyliczenie SCRIPT_ERROR_DEBUG_EXCEPTION_THROWN_KIND | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: b3aa4966-e110-4b30-b368-1281a9740dbd
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 997c5149467591a7612e6ff10b0efcc3efbc91bf
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/08/2019
ms.locfileid: "54087805"
---
# <a name="scripterrordebugexceptionthrownkind-enumeration"></a>Wyliczenie SCRIPT_ERROR_DEBUG_EXCEPTION_THROWN_KIND
Wskazuje rodzaj zgłaszanego wyjątku. To wyliczenie jest używane przez [IActiveScriptErrorDebug110::GetExceptionThrownKind](../../winscript/reference/iactivescripterrordebug110-getexceptionthrownkind.md) metody.  
  
> [!IMPORTANT]
>  Te stałe są implementowane przez program PDM w wersji 11.0 i nowszych. Znajduje się w zestawie activdbg100.h.  
  
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