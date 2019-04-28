---
title: IActiveScriptProfilerControl::SetProfilerEventMask | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScriptProfilerControl.SetProfilerEventMask
apilocation:
- scrobj.dll
ms.assetid: 207e192f-e12e-4fcb-b4d8-eaee50ecb86e
caps.latest.revision: 7
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 01e55d793d174f550e33e18558eccc19d417c80b
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62993093"
---
# <a name="iactivescriptprofilercontrolsetprofilereventmask"></a>IActiveScriptProfilerControl::SetProfilerEventMask
Ustawienie maski bitów 4-bajtowych, który określa typy zdarzeń, które powinny wywoływać silnik wykonywania skryptów.  
  
## <a name="syntax"></a>Składnia  
  
```cpp
HRESULT SetProfilerEventMask(  
    [in] DWORD dwEventMask);  
```  
  
#### <a name="parameters"></a>Parametry  
 `dwEventMask`  
 [in] Maska bitów do 4-bajtowych, który określa typy zdarzeń. Bity są zdefiniowane w [wyliczenie PROFILER_EVENT_MASK](../../winscript/reference/profiler-event-mask-enumeration.md).  
  
## <a name="return-value"></a>Wartość zwracana  
 Zwraca wartość HRESULT. Dopuszczalne są następujące wartości:  
  
|Wartość zwracana|Znaczenie|  
|------------------|-------------|  
|`S_OK`|Wykonanie metody powiodło się.|  
|`ACTIVPROF_E_PROFILER_ABSENT`|Profilowanie nie jest włączona.|  
  
## <a name="see-also"></a>Zobacz też  
 [IActiveScriptProfilerControl, interfejs](../../winscript/reference/iactivescriptprofilercontrol-interface.md)