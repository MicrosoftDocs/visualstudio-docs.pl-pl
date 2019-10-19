---
title: IActiveScriptProfilerControl2::P repareProfilerStop | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IActiveScriptProfilerControl2::PrepareProfilerStop
ms.assetid: e43a63bc-c44f-44a8-9db4-29062b9e6a16
caps.latest.revision: 5
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 24d4d73e0263882ad028ea66d3fac5e24f3af9ba
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2019
ms.locfileid: "72571447"
---
# <a name="iactivescriptprofilercontrol2prepareprofilerstop"></a>IActiveScriptProfilerControl2::PrepareProfilerStop
Powiadamia program profilujący o zatrzymaniu profilowania dla wszystkich odpowiednich aparatów skryptów. Korzystając z tej metody, można uzyskać kompletny stos wywołań, jeśli [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] jest uruchomiony po zatrzymaniu profilowania.  
  
## <a name="syntax"></a>Składnia  
  
```cpp
HRESULT PrepareProfilerStop();  
```  
  
#### <a name="parameters"></a>Parametry  
 Metoda nie przyjmuje żadnych parametrów.  
  
## <a name="return-value"></a>Wartość zwracana  
 Zwraca wartość HRESULT. Dopuszczalne są następujące wartości:  
  
|Wartość zwracana|Znaczenie|  
|------------------|-------------|  
|`S_OK`|Wykonanie metody powiodło się.|  
|`E_FAIL`|Nie można uruchomić profilowania.|  
|`S_FALSE`|Profilowanie zostało zatrzymane, gdy skrypt nie był uruchomiony.|  
|`ACTIVPROF_E_PROFILER_ABSENT`|Profilowanie nie jest włączone.|  
  
## <a name="remarks"></a>Uwagi  
 Wywołanie `IActiveScriptProfilerControl2::PrepareProfilerStop` zapewnia, że zdarzenia dla funkcji w stosie wywołań są wysyłane. Ta metoda musi być wywoływana przed zatrzymaniem profilowania na dowolnym aparacie skryptów, który znajduje się na bieżącej karcie. Metodę można wywołać dla dowolnego aparatu skryptów.  
  
## <a name="see-also"></a>Zobacz także  
 [IActiveScriptProfilerControl2:: CompleteProfilerStart](../../winscript/reference/iactivescriptprofilercontrol2-completeprofilerstart.md)    
 [IActiveScriptProfilerControl2, interfejs](../../winscript/reference/iactivescriptprofilercontrol2-interface.md)