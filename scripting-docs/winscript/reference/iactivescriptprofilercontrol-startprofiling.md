---
title: 'IActiveScriptProfilerControl:: StartProfiling | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScriptProfilerControl.StartProfiling
apilocation:
- scrobj.dll
ms.assetid: 56a7b3b7-8c21-43d0-9d8b-53bbc19fabb9
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: b37b60f50351496faceb97190ae0d173eba3a5f4
ms.sourcegitcommit: dcbb876a5dd598f2538e62e1eabd4dc98595b53a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/28/2019
ms.locfileid: "72983255"
---
# <a name="iactivescriptprofilercontrolstartprofiling"></a>IActiveScriptProfilerControl::StartProfiling
Uruchamia profilowanie w aparacie skryptów. Aparat tworzenia skryptów tworzy wystąpienie obiektu profilera, wykonując wywołanie funkcji [CoCreateInstance](/windows/desktop/api/combaseapi/nf-combaseapi-cocreateinstance).  
  
## <a name="syntax"></a>Składnia  
  
```cpp
HRESULT StartProfiling(  
    [in] REFCLSID clsidProfilerObject,  
    [in] DWORD dwEventMask,  
    [in] DWORD dwContext);  
```  
  
#### <a name="parameters"></a>Parametry  
 `clsidProfilerObject`  
 podczas Identyfikator klasy (CLSID) obiektu profilera, który ma zostać utworzony.  
  
 `dwEventMask`  
 podczas 4-bajtowa maska bitowa, która określa typy zdarzeń. Bity są zdefiniowane w [wyliczeniu PROFILER_EVENT_MASK](../../winscript/reference/profiler-event-mask-enumeration.md).  
  
 `dwContext`  
 podczas Wartość 4-bajtowa, która jest przesyłana do obiektu profilera.  
  
## <a name="return-value"></a>Wartość zwracana  
 Zwraca wartość HRESULT. Dopuszczalne są następujące wartości:  
  
|Wartość zwracana|Znaczenie|  
|------------------|-------------|  
|`S_OK`|Wykonanie metody powiodło się.|  
|`ACTIVPROF_E_PROFILER_PRESENT`|Profilowanie jest już włączone.|  
  
## <a name="see-also"></a>Zobacz także  
 [IActiveScriptProfilerControl, interfejs](../../winscript/reference/iactivescriptprofilercontrol-interface.md)