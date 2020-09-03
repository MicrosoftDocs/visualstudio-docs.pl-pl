---
title: 'IDebugCanStopEvent2:: Anuluj zatrzymanie | Microsoft Docs'
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "68191188"
---
# <a name="idebugcanstopevent2canstop"></a>IDebugCanStopEvent2::CanStop
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Powiadamia aparat debugowania (DE), czy ma zostać zatrzymany w bieżącej lokalizacji kodu, czy po prostu kontynuuje wykonywanie.  
  
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
 podczas Wartość niezerowa ( `TRUE` ), jeśli de powinna zatrzymać się w bieżącej lokalizacji kodu; w przeciwnym razie, zero ( `FALSE` ).  
  
## <a name="return-value"></a>Wartość zwracana  
 Jeśli powiedzie się, zwraca `S_OK` ; w przeciwnym razie zwraca kod błędu.  
  
## <a name="remarks"></a>Uwagi  
 Odbiorca tego zdarzenia zazwyczaj wywołuje metodę [getpowód](../../../extensibility/debugger/reference/idebugcanstopevent2-getreason.md) , aby ustalić przyczynę zatrzymania, a następnie wywołuje `IDebugCanStopEvent2::CanStop` metodę z odpowiednią odpowiedzią.  
  
 Jeśli ANULUJe, wysyła Zdarzenie opisujące powód zatrzymywania. Zazwyczaj są wysyłane dwa zdarzenia, czyli przerwanie użytkownika lub sygnału reprezentowane przez interfejs [IDebugBreakEvent2](../../../extensibility/debugger/reference/idebugbreakevent2.md) oraz zdarzenie punktu przerwania reprezentowane przez interfejs [IDebugBreakpointEvent2](../../../extensibility/debugger/reference/idebugbreakpointevent2.md) .  
  
## <a name="see-also"></a>Zobacz też  
 [IDebugCanStopEvent2](../../../extensibility/debugger/reference/idebugcanstopevent2.md)   
 [IDebugBreakEvent2](../../../extensibility/debugger/reference/idebugbreakevent2.md)   
 [IDebugBreakpointEvent2](../../../extensibility/debugger/reference/idebugbreakpointevent2.md)   
 [GetReason](../../../extensibility/debugger/reference/idebugcanstopevent2-getreason.md)
