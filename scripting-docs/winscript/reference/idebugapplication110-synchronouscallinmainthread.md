---
title: 'IDebugApplication110:: SynchronousCallInMainThread | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IDebugApplication110::SynchronousCallInMainThread
ms.assetid: 57475ae5-1520-45ef-800d-ccfc6235a5d1
caps.latest.revision: 5
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: db2b94d51cc5c9a65355aae7405fb162f564e0cc
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2019
ms.locfileid: "72573651"
---
# <a name="idebugapplication110synchronouscallinmainthread"></a>IDebugApplication110::SynchronousCallInMainThread
Wykonuje synchroniczne wywołanie na głównym wątku.  
  
> [!IMPORTANT]
> [Interfejs IDebugApplication110](../../winscript/reference/idebugapplication110-interface.md) jest implementowany przez PDM v 11.0 i nowsze. Znajduje się w zestawie activdbg100.h.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT SynchronousCallInMainThread([in] IDebugThreadCall* pptc, [in] DWORD_PTR dwParam1, [in] DWORD_PTR dwParam2, [in] DWORD_PTR dwParam3);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pptc`  
 Obiekt [interfejsu IDebugThreadCall](../../winscript/reference/idebugthreadcall-interface.md) do wywołania.  
  
 `dwParam1`  
 Pierwszy parametr wywołania.  
  
 `dwParam1`  
 Pierwszy parametr wywołania.  
  
 `dwParam2`  
 Drugi parametr wywołania.  
  
 `dwParam3`  
 Trzeci parametr wywołania.  
  
## <a name="see-also"></a>Zobacz także  
 [IDebugApplication110, interfejs](../../winscript/reference/idebugapplication110-interface.md)