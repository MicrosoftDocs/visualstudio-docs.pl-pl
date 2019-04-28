---
title: IDebugApplication110::AsynchronousCallInMainThread | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IDebugApplication110::AsynchronousCallInMainThread
ms.assetid: 13b80ff0-4bed-48c1-8031-d4147b51bf6c
caps.latest.revision: 6
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: d1b5e52d65a5fd70c4ec7de9ced9a0175940d93f
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "63446401"
---
# <a name="idebugapplication110asynchronouscallinmainthread"></a>IDebugApplication110::AsynchronousCallInMainThread
Sprawia, że wywołanie asynchroniczne w wątku głównym.  
  
> [!IMPORTANT]
> [Interfejs IDebugApplication110](../../winscript/reference/idebugapplication110-interface.md) jest implementowany przez program PDM w wersji 11.0 i nowszych. Znajduje się w zestawie activdbg100.h.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT AsynchronousCallInMainThread([in] IDebugThreadCall* pptc, [in] DWORD_PTR dwParam1, [in] DWORD_PTR dwParam2, [in] DWORD_PTR dwParam3);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pptc`  
 [Interfejs IDebugThreadCall](../../winscript/reference/idebugthreadcall-interface.md) obiekt do wywołania.  
  
 `dwParam1`  
 Pierwszy parametr wywołania.  
  
 `dwParam1`  
 Pierwszy parametr wywołania.  
  
 `dwParam2`  
 Drugi parametr wywołania.  
  
 `dwParam3`  
 Trzeci parametr wywołania.  
  
## <a name="see-also"></a>Zobacz też  
 [IDebugApplication110, interfejs](../../winscript/reference/idebugapplication110-interface.md)