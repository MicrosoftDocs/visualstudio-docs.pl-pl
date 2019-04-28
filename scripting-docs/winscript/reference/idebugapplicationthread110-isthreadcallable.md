---
title: IDebugApplicationThread110::IsThreadCallable | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IDebugApplicationThread110::IsThreadCallable
ms.assetid: 2a75a366-801d-47e0-bba3-51aa669e03a7
caps.latest.revision: 5
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 90f0010a513adef67af1285ac15bc35d4573df57
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "63440513"
---
# <a name="idebugapplicationthread110isthreadcallable"></a>IDebugApplicationThread110::IsThreadCallable
Określa, czy ten wątek jest w stanie, który przetworzy wywołań za pomocą wątku menedżerów PDM przełączanie mechanizmów, takich jak SynchronousCallInThread.  
  
> [!IMPORTANT]
> [Interfejs IDebugApplicationThread110](../../winscript/reference/idebugapplicationthread110-interface.md) jest implementowany przez program PDM w wersji 11.0 i nowszych. Znajduje się w zestawie activdbg100.h.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT IsThreadCallable([out, annotation("_Out_")] BOOL * pfIsCallable);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pfIsCallable`  
 [out] `true` Jeśli wątek jest wywoływane, w przeciwnym razie `false`.  
  
## <a name="see-also"></a>Zobacz też  
 [IDebugApplicationThread110, interfejs](../../winscript/reference/idebugapplicationthread110-interface.md)