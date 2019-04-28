---
title: IRemoteDebugApplication110::GetMainThread | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IRemoteDebugApplication110::GetMainThread
ms.assetid: 9982acc9-3d35-4dcf-8ca9-662469de4072
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 8a4b51d87f89d77bebf065ce5f52a297ada333d3
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "63383504"
---
# <a name="iremotedebugapplication110getmainthread"></a>IRemoteDebugApplication110::GetMainThread
Zwraca główny wątek dla hostów, które wywołują [setsite —](http://go.microsoft.com/fwlink/?LinkId=232439), w przeciwnym razie zwraca E_FAIL.  
  
> [!IMPORTANT]
> [Interfejs IRemoteDebugApplication](../../winscript/reference/iremotedebugapplication-interface.md) jest implementowany przez program PDM w wersji 11.0 i nowszych. Znajduje się w zestawie activdbg100.h.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT GetMainThread([out] IRemoteDebugApplicationThread **ppThread);  
```  
  
#### <a name="parameters"></a>Parametry  
 `ppThread`  
 [out] Głównym [interfejs IRemoteDebugApplicationThread](../../winscript/reference/iremotedebugapplicationthread-interface.md).  
  
## <a name="see-also"></a>Zobacz też  
 [IRemoteDebugApplication Interface](../../winscript/reference/iremotedebugapplication-interface.md)   
 [IRemoteDebugApplication110, interfejs](../../winscript/reference/iremotedebugapplication110-interface.md)