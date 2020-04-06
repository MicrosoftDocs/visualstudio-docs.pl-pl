---
title: IDebugCanStopEvent2::GetReason | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugCanStopEvent2::GetReason
helpviewer_keywords:
- IDebugCanStopEvent2::GetReason
ms.assetid: f5de31ca-7b8d-4029-9cf9-ba860ac66af6
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 59e611c3ed69528f92a6085cf74aa44efed09144
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80734522"
---
# <a name="idebugcanstopevent2getreason"></a>IDebugCanStopEvent2::GetReason
Pobiera powód, dla którego aparat debugowania (DE) chce zatrzymać.

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
[na zewnątrz] Zwraca wartość z wyliczenia [CANSTOP_REASON,](../../../extensibility/debugger/reference/canstop-reason.md) który opisuje przyczynę tego zdarzenia.

## <a name="return-value"></a>Wartość zwracana
 Jeśli się `S_OK`powiedzie, zwraca ; w przeciwnym razie zwraca kod błędu.

## <a name="remarks"></a>Uwagi
 Ta metoda jest zazwyczaj wywoływana przed [CanStop](../../../extensibility/debugger/reference/idebugcanstopevent2-canstop.md) metody, więc wywołujący`TRUE`można określić, czy przekazać non-zero ( ) do `IDebugCanStopEvent2::CanStop` metody.

 Powodem zatrzymania może być `CANSTOP_ENTRYPOINT`albo , co oznacza, że `CANSTOP_STEPIN`DE osiągnęła punkt wejścia, lub , co oznacza, że DE wszedł do funkcji.

## <a name="see-also"></a>Zobacz też
- [IDebugCanStopEvent2](../../../extensibility/debugger/reference/idebugcanstopevent2.md)
- [CANSTOP_REASON](../../../extensibility/debugger/reference/canstop-reason.md)
- [CanStop](../../../extensibility/debugger/reference/idebugcanstopevent2-canstop.md)
