---
description: Pobiera przyczynę zatrzymania aparatu debugowania.
title: 'IDebugCanStopEvent2:: getpowód | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugCanStopEvent2::GetReason
helpviewer_keywords:
- IDebugCanStopEvent2::GetReason
ms.assetid: f5de31ca-7b8d-4029-9cf9-ba860ac66af6
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 2125bb90693d5a4c5cc23ac1225d56dea636de2e
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/25/2021
ms.locfileid: "105085055"
---
# <a name="idebugcanstopevent2getreason"></a>IDebugCanStopEvent2::GetReason
Pobiera przyczynę zatrzymania aparatu debugowania.

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

## <a name="parameters"></a>Parametry
`pcr`\
określoną Zwraca wartość z wyliczenia [CANSTOP_REASON](../../../extensibility/debugger/reference/canstop-reason.md) opisującą przyczynę tego zdarzenia.

## <a name="return-value"></a>Wartość zwracana
 Jeśli powiedzie się, zwraca `S_OK` ; w przeciwnym razie zwraca kod błędu.

## <a name="remarks"></a>Uwagi
 Ta metoda jest zazwyczaj wywoływana przed wywołaniem [metody,](../../../extensibility/debugger/reference/idebugcanstopevent2-canstop.md) aby obiekt wywołujący mógł określić, czy przekazywać wartość różną od zera ( `TRUE` ) do `IDebugCanStopEvent2::CanStop` metody.

 Powodem zatrzymywania może być albo `CANSTOP_ENTRYPOINT` , co oznacza, że de osiągnął punkt wejścia, lub `CANSTOP_STEPIN` , co oznacza, że de został przeciągnięty do funkcji.

## <a name="see-also"></a>Zobacz też
- [IDebugCanStopEvent2](../../../extensibility/debugger/reference/idebugcanstopevent2.md)
- [CANSTOP_REASON](../../../extensibility/debugger/reference/canstop-reason.md)
- [CanStop](../../../extensibility/debugger/reference/idebugcanstopevent2-canstop.md)
