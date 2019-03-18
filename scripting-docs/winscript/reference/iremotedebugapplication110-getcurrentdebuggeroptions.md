---
title: IRemoteDebugApplication110::GetCurrentDebuggerOptions | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IRemoteDebugApplication110::GetCurrentDebuggerOptions
ms.assetid: a6e9cae1-e8f3-4d62-b133-52e9ca12ba7a
caps.latest.revision: 5
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 61504206913006b12d55ae8d8df8b08389875095
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2019
ms.locfileid: "58157402"
---
# <a name="iremotedebugapplication110getcurrentdebuggeroptions"></a>IRemoteDebugApplication110::GetCurrentDebuggerOptions
Zwraca zestaw opcji, które są obecnie włączone.  
  
> [!IMPORTANT]
>  [Interfejs IRemoteDebugApplication](../../winscript/reference/iremotedebugapplication-interface.md) jest implementowany przez program PDM w wersji 11.0 i nowszych. Znajduje się w zestawie activdbg100.h.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT GetCurrentDebuggerOptions([out] enum SCRIPT_DEBUGGER_OPTIONS* pCurrentOptions);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pCurrentOptions`  
 [out] Bieżące opcje.  
  
## <a name="see-also"></a>Zobacz też  
 [IRemoteDebugApplication Interface](../../winscript/reference/iremotedebugapplication-interface.md)   
 [IRemoteDebugApplication110, interfejs](../../winscript/reference/iremotedebugapplication110-interface.md)