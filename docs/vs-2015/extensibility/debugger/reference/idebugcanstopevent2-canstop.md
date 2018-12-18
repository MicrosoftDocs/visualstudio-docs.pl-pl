---
title: IDebugCanStopEvent2::CanStop | Dokumentacja firmy Microsoft
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
- IDebugCanStopEvent2::CanStop
helpviewer_keywords:
- IDebugCanStopEvent2::CanStop
ms.assetid: 7d61adbe-6b3d-41f3-86a1-45d9cc01a7f8
caps.latest.revision: 11
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: c0b89f694d544cc622ee63f87c77e2ddaf8646d3
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/16/2018
ms.locfileid: "51745427"
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

