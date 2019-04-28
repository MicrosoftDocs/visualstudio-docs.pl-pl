---
title: IDebugApplicationThread110::AsynchronousCallIntoThread | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: 06b3031a-4aec-4a47-afaa-04642a4c4870
caps.latest.revision: 2
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: fd9fe0b7177c95aec675faaaa85896c52b375084
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "63440555"
---
# <a name="idebugapplicationthread110asynchronouscallintothread"></a>IDebugApplicationThread110::AsynchronousCallIntoThread
Sprawia, że wywołanie asynchroniczne w wątku głównym.  
  
> [!IMPORTANT]
> [Interfejs IDebugApplicationThread110](../../winscript/reference/idebugapplicationthread110-interface.md) jest implementowany przez program PDM w wersji 11.0 i nowszych. Znajduje się w zestawie activdbg100.h.  
  
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