---
title: IActiveScriptProfilerCallback::Initialize | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScriptProfilerCallback.Initialize
apilocation:
- scrobj.dll
ms.assetid: a257111e-a50b-4962-9dd6-c893d40f6985
caps.latest.revision: 10
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 66ef6dc37e1f2f8117e440089ee36958d616dda0
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62993361"
---
# <a name="iactivescriptprofilercallbackinitialize"></a>IActiveScriptProfilerCallback::Initialize
Wywoływane w celu zainicjowania obiektu profiler, zawsze wtedy, gdy rozpoczęto profilowanie na silnik wykonywania skryptów.  
  
## <a name="syntax"></a>Składnia  
  
```cpp
HRESULT Initialize(  
    [in] DWORD dwContext);  
```  
  
#### <a name="parameters"></a>Parametry  
 `dwContext`  
 [in] 4-bajtową wartość, który jest przekazywany do [IActiveScriptProfilerControl::StartProfiling](../../winscript/reference/iactivescriptprofilercontrol-startprofiling.md).  
  
## <a name="return-value"></a>Wartość zwracana  
 Zwraca wartość HRESULT. Dopuszczalne są następujące wartości:  
  
|Wartość zwracana|Znaczenie|  
|------------------|-------------|  
|`S_OK`|Wykonanie metody powiodło się.|  
  
## <a name="remarks"></a>Uwagi  
 Jeśli metoda nie można zainicjować obiektu profiler, powinien zostać zwrócony błąd HRESULT do powiadamiania silnik wykonywania skryptów. W tym przypadku bezpośrednio wywołać aparat skryptów [IActiveScriptProfilerCallback::Shutdown](../../winscript/reference/iactivescriptprofilercallback-shutdown.md), przekazując HRESULT w parametrze, a następnie zwolnij obiekt profiler.  
  
## <a name="see-also"></a>Zobacz też  
 [IActiveScriptProfilerCallback, interfejs](../../winscript/reference/iactivescriptprofilercallback-interface.md)