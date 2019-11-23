---
title: 'IRemoteDebugApplication110:: SetDebuggerOptions | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IRemoteDebugApplication110::SetDebuggerOptions
ms.assetid: 58e9fd18-3e0d-47fa-8893-f316146bde84
caps.latest.revision: 5
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: e7168a4ef8ec70368c0ff691ba1f721275f9d65d
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2019
ms.locfileid: "72577423"
---
# <a name="iremotedebugapplication110setdebuggeroptions"></a>IRemoteDebugApplication110::SetDebuggerOptions
Wywołuje się, by zaktualizować opcje debugera. Ta metoda powinna być wywoływana po [IRemoteDebugApplication:: ConnectDebugger](../../winscript/reference/iremotedebugapplication-connectdebugger.md). Metoda [IRemoteDebugApplication::D isconnectdebugger](../../winscript/reference/iremotedebugapplication-disconnectdebugger.md) automatycznie przywraca domyślne opcje. Opcje domyślne to 0 (SDO_NONE).  
  
> [!IMPORTANT]
> [Interfejs IRemoteDebugApplication](../../winscript/reference/iremotedebugapplication-interface.md) jest implementowany przez PDM v 11.0 i nowsze. Znajduje się w zestawie activdbg100.h.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT SetDebuggerOptions(        [in] enum SCRIPT_DEBUGGER_OPTIONS mask,        [in] enum SCRIPT_DEBUGGER_OPTIONS value    );  
```  
  
#### <a name="parameters"></a>Parametry  
 `mask`  
 SCRIPT_DEBUGGER_OPTIONS maskę [wyliczenia](../../winscript/reference/script-debugger-options-enumeration.md) .  
  
 `value`  
 Wartość [wyliczenia SCRIPT_DEBUGGER_OPTIONS](../../winscript/reference/script-debugger-options-enumeration.md) .  
  
## <a name="see-also"></a>Zobacz także  
 [IRemoteDebugApplication  interfejsu](../../winscript/reference/iremotedebugapplication-interface.md)  
 [IRemoteDebugApplication110, interfejs](../../winscript/reference/iremotedebugapplication110-interface.md)