---
title: IActiveScriptProfilerControl2::CompleteProfilerStart | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IActiveScriptProfilerControl2::CompleteProfilerStart
ms.assetid: e14d94a2-39d3-40a1-84d9-6300fbe2b339
caps.latest.revision: 5
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 36a1f5d6a1401e2860b65a29c8e383627e83c6be
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62993027"
---
# <a name="iactivescriptprofilercontrol2completeprofilerstart"></a>IActiveScriptProfilerControl2::CompleteProfilerStart
Powiadamia program profilujący do profilowania na wszystkich odpowiednich aparatów obsługi skryptów. Za pomocą tej metody, można uzyskać pełny stos wywołań, jeśli [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] działa w przypadku uruchamiania profilowania.  
  
## <a name="syntax"></a>Składnia  
  
```cpp
HRESULT CompleteProfilerStart();  
```  
  
#### <a name="parameters"></a>Parametry  
 Metoda nie przyjmuje żadnych parametrów.  
  
## <a name="return-value"></a>Wartość zwracana  
 Zwraca wartość HRESULT. Dopuszczalne są następujące wartości:  
  
|Wartość zwracana|Znaczenie|  
|------------------|-------------|  
|`S_OK`|Wykonanie metody powiodło się.|  
|`E_FAIL`|Nie można rozpocząć profilowania.|  
|`S_FALSE`|Profilowanie uruchomienia skryptu nie zostało uruchomione.|  
|`ACTIVPROF_E_PROFILER_ABSENT`|Profilowanie nie jest włączona. Ustawiono bez wywołania zwrotnego.|  
|`E_OUTOFMEMORY`|Nie można uzyskać stosu wywołań ze względu na stan braku pamięci.|  
  
## <a name="remarks"></a>Uwagi  
 Wywoływanie `IActiveScriptProfilerControl2::CompleteProfilerStart` gwarantuje, że zdarzenia dla funkcji już w stosie wywołań są wysyłane. Ta metoda musi być wywoływana po profilowaniu rozpoczyna się silnik wykonywania skryptów, który znajduje się w bieżącej karcie. Metodę można wywołać dla dowolnego aparatu obsługi skryptów.  
  
## <a name="see-also"></a>Zobacz też  
 [IActiveScriptProfilerControl2::PrepareProfilerStop](../../winscript/reference/iactivescriptprofilercontrol2-prepareprofilerstop.md)   
 [IActiveScriptProfilerControl2, interfejs](../../winscript/reference/iactivescriptprofilercontrol2-interface.md)