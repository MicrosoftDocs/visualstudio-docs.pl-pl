---
title: IActiveScriptProfilerControl2::PrepareProfilerStop | Microsoft Docs
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
ms.openlocfilehash: 11a32f36ec6eddcc06faa77e093f19e8df503fa4
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2019
ms.locfileid: "58149318"
---
# <a name="iactivescriptprofilercontrol2prepareprofilerstop"></a>IActiveScriptProfilerControl2::PrepareProfilerStop
Powiadamia program profilujący zamierza zatrzymanie profilowania w wszystkich odpowiednich aparatów obsługi skryptów. Za pomocą tej metody, można uzyskać pełny stos wywołań, jeśli [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] działa po zatrzymaniu profilowania.  
  
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
|`E_FAIL`|Nie można uruchomić profilowanie.|  
|`S_FALSE`|Profilowanie zostało zatrzymane, gdy skrypt nie została uruchomiona.|  
|`ACTIVPROF_E_PROFILER_ABSENT`|Profilowanie nie jest włączona.|  
  
## <a name="remarks"></a>Uwagi  
 Wywoływanie `IActiveScriptProfilerControl2::PrepareProfilerStop` gwarantuje, że zdarzenia dla funkcji w stosie wywołań są wysyłane. Ta metoda musi być wywoływana przed zatrzymaniem profilowania w silnik wykonywania skryptów, który znajduje się w bieżącej karcie. Metodę można wywołać dla dowolnego aparatu obsługi skryptów.  
  
## <a name="see-also"></a>Zobacz też  
 [IActiveScriptProfilerControl2::CompleteProfilerStart](../../winscript/reference/iactivescriptprofilercontrol2-completeprofilerstart.md)   
 [IActiveScriptProfilerControl2, interfejs](../../winscript/reference/iactivescriptprofilercontrol2-interface.md)