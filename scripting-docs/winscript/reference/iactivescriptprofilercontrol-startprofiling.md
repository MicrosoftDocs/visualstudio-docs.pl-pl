---
title: IActiveScriptProfilerControl::StartProfiling | Dokumentacja firmy Microsoft
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
ms.openlocfilehash: 780886e4ca21abbe11580992244cee0d6a28b134
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62993140"
---
# <a name="iactivescriptprofilercontrolstartprofiling"></a>IActiveScriptProfilerControl::StartProfiling
Rozpoczyna się profilowanie na silnik wykonywania skryptów. Aparat skryptów tworzy wystąpienie obiektu profiler poprzez wywołanie [CoCreateInstance](https://docs.microsoft.com/windows/desktop/api/combaseapi/nf-combaseapi-cocreateinstance).  
  
## <a name="syntax"></a>Składnia  
  
```cpp
HRESULT StartProfiling(  
    [in] REFCLSID clsidProfilerObject,  
    [in] DWORD dwEventMask,  
    [in] DWORD dwContext);  
```  
  
#### <a name="parameters"></a>Parametry  
 `clsidProfilerObject`  
 [in] Klasa identyfikator (CLSID) obiekt profiler, który ma zostać utworzony.  
  
 `dwEventMask`  
 [in] Maska bitów do 4-bajtowych, który określa typy zdarzeń. Bity są zdefiniowane w [wyliczenie PROFILER_EVENT_MASK](../../winscript/reference/profiler-event-mask-enumeration.md).  
  
 `dwContext`  
 [in] Wartość 4-bajtowych, który jest przekazywany do obiektu profilera.  
  
## <a name="return-value"></a>Wartość zwracana  
 Zwraca wartość HRESULT. Dopuszczalne są następujące wartości:  
  
|Wartość zwracana|Znaczenie|  
|------------------|-------------|  
|`S_OK`|Wykonanie metody powiodło się.|  
|`ACTIVPROF_E_PROFILER_PRESENT`|Profilowanie jest już włączony.|  
  
## <a name="see-also"></a>Zobacz też  
 [IActiveScriptProfilerControl, interfejs](../../winscript/reference/iactivescriptprofilercontrol-interface.md)