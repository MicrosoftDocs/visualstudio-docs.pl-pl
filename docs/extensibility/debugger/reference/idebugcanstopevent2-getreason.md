---
title: IDebugCanStopEvent2::GetReason | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugCanStopEvent2::GetReason
helpviewer_keywords:
- IDebugCanStopEvent2::GetReason
ms.assetid: f5de31ca-7b8d-4029-9cf9-ba860ac66af6
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 4f253fc622beb6eee3490b77a1531b0b2096f14a
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62877046"
---
# <a name="idebugcanstopevent2getreason"></a>IDebugCanStopEvent2::GetReason
Pobiera powód, dlaczego aparat debugowania (DE) chce, aby zatrzymać.

## <a name="syntax"></a>Składnia

```cpp
HRESULT GetReason( 
   CANSTOP_REASON* pcr
);
```

```csharp
int GetReason( 
   out enum_CANSTOP_REASON pcr
);
```

#### <a name="parameters"></a>Parametry
 `pcr`

 [out] Zwraca wartość z zakresu od [CANSTOP_REASON](../../../extensibility/debugger/reference/canstop-reason.md) wyliczenie opisujące przyczynę tego zdarzenia.

## <a name="return-value"></a>Wartość zwracana
 Jeśli operacja się powiedzie, zwraca `S_OK`; w przeciwnym razie zwraca kod błędu.

## <a name="remarks"></a>Uwagi
 Ta metoda jest zazwyczaj wywoływana przed [wartości właściwości CanStop](../../../extensibility/debugger/reference/idebugcanstopevent2-canstop.md) metody, dzięki czemu elementu wywołującego można określić, czy przekazywać różna od zera (`TRUE`) do `IDebugCanStopEvent2::CanStop` metody.

 Przyczyna zatrzymania może być `CANSTOP_ENTRYPOINT`, co oznacza, że Niemcy został osiągnięty punkt wejścia lub `CANSTOP_STEPIN`, co oznacza, że Niemcy opuścił do funkcji.

## <a name="see-also"></a>Zobacz też
- [IDebugCanStopEvent2](../../../extensibility/debugger/reference/idebugcanstopevent2.md)
- [CANSTOP_REASON](../../../extensibility/debugger/reference/canstop-reason.md)
- [CanStop](../../../extensibility/debugger/reference/idebugcanstopevent2-canstop.md)