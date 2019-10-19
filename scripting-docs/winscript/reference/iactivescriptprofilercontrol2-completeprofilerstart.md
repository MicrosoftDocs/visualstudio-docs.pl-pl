---
title: 'IActiveScriptProfilerControl2:: CompleteProfilerStart | Microsoft Docs'
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
ms.openlocfilehash: f0230ecb480792b5b24b7375f5b95926735d0a61
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2019
ms.locfileid: "72571556"
---
# <a name="iactivescriptprofilercontrol2completeprofilerstart"></a>IActiveScriptProfilerControl2::CompleteProfilerStart
Powiadamia program profilujący o rozpoczęciu profilowania dla wszystkich odpowiednich aparatów skryptów. Korzystając z tej metody, można uzyskać kompletny stos wywołań, jeśli [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] jest uruchomiona po rozpoczęciu profilowania.  
  
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
|`E_FAIL`|Nie można uruchomić profilowania.|  
|`S_FALSE`|Profilowanie zostało uruchomione, gdy skrypt nie był uruchomiony.|  
|`ACTIVPROF_E_PROFILER_ABSENT`|Profilowanie nie jest włączone. Nie ustawiono wywołania zwrotnego.|  
|`E_OUTOFMEMORY`|Nie można uzyskać stosu wywołań ze względu na stan braku pamięci.|  
  
## <a name="remarks"></a>Uwagi  
 Wywołanie `IActiveScriptProfilerControl2::CompleteProfilerStart` gwarantuje, że zdarzenia dla funkcji znajdujących się już w stosie wywołań są wysyłane. Ta metoda musi być wywoływana po uruchomieniu profilowania na dowolnym aparacie skryptów, który znajduje się na bieżącej karcie. Metodę można wywołać dla dowolnego aparatu skryptów.  
  
## <a name="see-also"></a>Zobacz także  
 [IActiveScriptProfilerControl2::P repareprofilerstop](../../winscript/reference/iactivescriptprofilercontrol2-prepareprofilerstop.md)    
 [IActiveScriptProfilerControl2, interfejs](../../winscript/reference/iactivescriptprofilercontrol2-interface.md)