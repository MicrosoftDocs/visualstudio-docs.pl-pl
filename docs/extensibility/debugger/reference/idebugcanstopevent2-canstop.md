---
title: IDebugCanStopEvent2::CanStop | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugCanStopEvent2::CanStop
helpviewer_keywords:
- IDebugCanStopEvent2::CanStop
ms.assetid: 7d61adbe-6b3d-41f3-86a1-45d9cc01a7f8
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 307b6d25f2e45276ead7c4b360ae191a01059104
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62876972"
---
# <a name="idebugcanstopevent2canstop"></a>IDebugCanStopEvent2::CanStop
Powiadamia aparat debugowania (DE), czy należy zatrzymać w bieżącej lokalizacji kodu lub po prostu kontynuowanie wykonywania.

## <a name="syntax"></a>Składnia

```cpp
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
- [IDebugCanStopEvent2](../../../extensibility/debugger/reference/idebugcanstopevent2.md)
- [IDebugBreakEvent2](../../../extensibility/debugger/reference/idebugbreakevent2.md)
- [IDebugBreakpointEvent2](../../../extensibility/debugger/reference/idebugbreakpointevent2.md)
- [GetReason](../../../extensibility/debugger/reference/idebugcanstopevent2-getreason.md)