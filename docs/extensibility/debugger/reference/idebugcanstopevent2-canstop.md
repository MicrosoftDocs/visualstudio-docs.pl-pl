---
title: IDebugCanStopEvent2::CanStop | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugCanStopEvent2::CanStop
helpviewer_keywords:
- IDebugCanStopEvent2::CanStop
ms.assetid: 7d61adbe-6b3d-41f3-86a1-45d9cc01a7f8
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 2915938c966bac7f842d0745c973c7d0b7033e2b
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80734592"
---
# <a name="idebugcanstopevent2canstop"></a>IDebugCanStopEvent2::CanStop
Powiadamia aparat debugowania (DE), czy zatrzymać się w bieżącej lokalizacji kodu lub po prostu kontynuować wykonywanie.

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

## <a name="parameters"></a>Parametry
`fCanStop`\
[w] Non-zero`TRUE`( ), jeśli DE powinien zatrzymać się w bieżącej lokalizacji kodu; w przeciwnym`FALSE`razie zero ( ).

## <a name="return-value"></a>Wartość zwracana
 Jeśli się `S_OK`powiedzie, zwraca ; w przeciwnym razie zwraca kod błędu.

## <a name="remarks"></a>Uwagi
 Odbiornik tego zdarzenia zazwyczaj wywołuje [GetReason](../../../extensibility/debugger/reference/idebugcanstopevent2-getreason.md) metody, aby określić przyczynę DE chce `IDebugCanStopEvent2::CanStop` zatrzymać, a następnie wywołuje metodę z odpowiednią odpowiedzią.

 Jeśli DE zatrzymuje, wysyła zdarzenie, które opisuje przyczynę zatrzymania. Zazwyczaj są dwa zdarzenia, które są wysyłane, przerwa użytkownika lub sygnału reprezentowane przez interfejs [IDebugBreakEvent2](../../../extensibility/debugger/reference/idebugbreakevent2.md) i zdarzenie punktu przerwania reprezentowane przez interfejs [IDebugBreakpointEvent2.](../../../extensibility/debugger/reference/idebugbreakpointevent2.md)

## <a name="see-also"></a>Zobacz też
- [IDebugCanStopEvent2](../../../extensibility/debugger/reference/idebugcanstopevent2.md)
- [IDebugBreakEvent2](../../../extensibility/debugger/reference/idebugbreakevent2.md)
- [IDebugBreakpointEvent2](../../../extensibility/debugger/reference/idebugbreakpointevent2.md)
- [GetReason](../../../extensibility/debugger/reference/idebugcanstopevent2-getreason.md)
