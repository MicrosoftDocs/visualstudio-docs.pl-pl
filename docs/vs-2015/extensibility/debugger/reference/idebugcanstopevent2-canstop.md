---
title: IDebugCanStopEvent2::CanStop | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugCanStopEvent2::CanStop
helpviewer_keywords:
- IDebugCanStopEvent2::CanStop
ms.assetid: 7d61adbe-6b3d-41f3-86a1-45d9cc01a7f8
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 8167013489b3b37e254100f7547cd61d54529b95
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54788434"
---
# <a name="idebugcanstopevent2canstop"></a>IDebugCanStopEvent2::CanStop
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Powiadamia aparat debugowania (DE), czy należy zatrzymać w bieżącej lokalizacji kodu lub po prostu kontynuowanie wykonywania.  
  
## <a name="syntax"></a>Składnia  
  
```cpp#  
HRESULT CanStop (   
   BOOL fCanStop  
);  
```  
  
```csharp  
int CanStop (   
   int fCanStop  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `fCanStop`  
 [in] Niezerowa Koniunkcja (`TRUE`) jeżeli DE powinna zostać przerwana w bieżącej lokalizacji kodu; w przeciwnym wypadku zero (`FALSE`).  
  
## <a name="return-value"></a>Wartość zwracana  
 Jeśli operacja się powiedzie, zwraca `S_OK`; w przeciwnym razie zwraca kod błędu.  
  
## <a name="remarks"></a>Uwagi  
 Odbiornik zdarzenia zwykle nie wywoła [getreason —](../../../extensibility/debugger/reference/idebugcanstopevent2-getreason.md) metodę, aby zidentyfikować przyczynę DE chce, aby zatrzymać, a następnie wywołania `IDebugCanStopEvent2::CanStop` metody z właściwą odpowiedź.  
  
 Jeśli zatrzymuje się DE wysyła zdarzenia opisujące przyczynę zatrzymywania. Zazwyczaj są dwa zdarzenia, które są wysyłane, użytkownika lub sygnał przerwania, reprezentowane przez [IDebugBreakEvent2](../../../extensibility/debugger/reference/idebugbreakevent2.md) interfejsu i zdarzenie punktu przerwania reprezentowany przez [IDebugBreakpointEvent2](../../../extensibility/debugger/reference/idebugbreakpointevent2.md) interfejsu.  
  
## <a name="see-also"></a>Zobacz też  
 [IDebugCanStopEvent2](../../../extensibility/debugger/reference/idebugcanstopevent2.md)   
 [IDebugBreakEvent2](../../../extensibility/debugger/reference/idebugbreakevent2.md)   
 [IDebugBreakpointEvent2](../../../extensibility/debugger/reference/idebugbreakpointevent2.md)   
 [GetReason](../../../extensibility/debugger/reference/idebugcanstopevent2-getreason.md)
