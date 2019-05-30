---
title: IDebugCanStopEvent2::CanStop | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugCanStopEvent2::CanStop
helpviewer_keywords:
- IDebugCanStopEvent2::CanStop
ms.assetid: 7d61adbe-6b3d-41f3-86a1-45d9cc01a7f8
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: ab59cf5d077c4e397373c4c86b864ed17749fc19
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/29/2019
ms.locfileid: "66351258"
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

## <a name="parameters"></a>Parametry
`fCanStop`\
[in] Niezerowa Koniunkcja (`TRUE`) jeżeli DE powinna zostać przerwana w bieżącej lokalizacji kodu; w przeciwnym wypadku zero (`FALSE`).

## <a name="return-value"></a>Wartość zwracana
 Jeśli operacja się powiedzie, zwraca `S_OK`; w przeciwnym razie zwraca kod błędu.

## <a name="remarks"></a>Uwagi
 Odbiornik zdarzenia zwykle nie wywoła [getreason —](../../../extensibility/debugger/reference/idebugcanstopevent2-getreason.md) metodę, aby zidentyfikować przyczynę DE chce, aby zatrzymać, a następnie wywołania `IDebugCanStopEvent2::CanStop` metody z właściwą odpowiedź.

 Jeśli zatrzymuje się DE wysyła zdarzenia opisujące przyczynę zatrzymywania. Zazwyczaj są dwa zdarzenia, które są wysyłane, użytkownika lub sygnał przerwania, reprezentowane przez [IDebugBreakEvent2](../../../extensibility/debugger/reference/idebugbreakevent2.md) interfejsu i zdarzenie punktu przerwania reprezentowany przez [IDebugBreakpointEvent2](../../../extensibility/debugger/reference/idebugbreakpointevent2.md) interfejsu.

## <a name="see-also"></a>Zobacz także
- [IDebugCanStopEvent2](../../../extensibility/debugger/reference/idebugcanstopevent2.md)
- [IDebugBreakEvent2](../../../extensibility/debugger/reference/idebugbreakevent2.md)
- [IDebugBreakpointEvent2](../../../extensibility/debugger/reference/idebugbreakpointevent2.md)
- [GetReason](../../../extensibility/debugger/reference/idebugcanstopevent2-getreason.md)