---
title: IDebugProcess2::Attach | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IDebugProcess2::Attach
helpviewer_keywords:
- IDebugProcess2::Attach
ms.assetid: 40d78417-fde2-45c3-96c9-16e06bd9008d
caps.latest.revision: 11
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: e2b9c3e4bfbcc9604c5fe415a169cbce0a32a98e
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/16/2018
ms.locfileid: "51761857"
---
# <a name="idebugprocess2attach"></a>IDebugProcess2::Attach
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Dołącza Menedżer debugowania sesji (SDM) do procesu.  
  
## <a name="syntax"></a>Składnia  
  
```cpp#  
HRESULT Attach(   
   IDebugEventCallback2* pCallback,  
   GUID*                 rgguidSpecificEngines,  
   DWORD                 celtSpecificEngines,  
   HRESULT*              rghrEngineAttach  
);  
```  
  
```csharp  
int Attach(   
   IDebugEventCallback2 pCallback,  
   Guid[]               rgguidSpecificEngines,  
   uint                 celtSpecificEngines,  
   int[]                rghrEngineAttach  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pCallback`  
 [in] [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) obiekt, który jest używany dla powiadomień o zdarzeniach debugowania.  
  
 `rgguidSpecificEngines`  
 [in] Tablica identyfikatorów GUID z aparatami debugowania można używać do debugowania programów uruchomionych w procesie. Ten parametr może być wartością null. Aby uzyskać szczegółowe informacje, zobacz uwagi.  
  
 `celtSpecificEngines`  
 [in] Liczba debugowania aparatów w `rgguidSpecificEngines` macierzy i rozmiar `rghrEngineAttach` tablicy.  
  
 `rghrEngineAttach`  
 [out w] Tablica kody HRESULT zwracane przez aparaty debugowania. Rozmiar tej tablicy jest określona w `celtSpecificEngines` parametru. Każdy kod jest zwykle `S_OK` lub `S_ATTACH_DEFERRED`. Te ostatnie wskazuje, że Niemcy jest obecnie dołączony do żadnych programów.  
  
## <a name="return-value"></a>Wartość zwracana  
 Jeśli operacja się powiedzie, zwraca `S_OK`; w przeciwnym razie zwraca kod błędu. W poniższej tabeli przedstawiono inne możliwe wartości.  
  
|Wartość|Opis|  
|-----------|-----------------|  
|`E_ATTACH_DEBUGGER_ALREADY_ATTACHED`|Określony proces jest już dołączony do debugera.|  
|`E_ATTACH_DEBUGGEE_PROCESS_SECURITY_VIOLATION`|Wystąpiło naruszenie zabezpieczeń podczas wykonywania procedury dołączania.|  
|`E_ATTACH_CANNOT_ATTACH_TO_DESKTOP`|Nie można dołączyć pulpitu procesu do debugera.|  
  
## <a name="remarks"></a>Uwagi  
 Dołączanie do procesu dołącza SDM do wszystkich programów uruchomionych w tym procesie, który może być debugowany przez aparaty debugowania (DE) określona w `rgguidSpecificEngines` tablicy. Ustaw `rgguidSpecificEngines` parametru o wartości null, lub Uwzględnij wartość `GUID_NULL` w tablicy do dołączenia do wszystkich programów w procesie.  
  
 Wszystkie zdarzenia debugowania, które wystąpiły w procesie są wysyłane do danego [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) obiektu. To `IDebugEventCallback2` obiektu jest udostępniane po SDM wywołuje tę metodę.  
  
## <a name="see-also"></a>Zobacz też  
 [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)   
 [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)

