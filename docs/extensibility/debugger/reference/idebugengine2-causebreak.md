---
title: IDebugEngine2::CauseBreak | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEngine2::CauseBreak
helpviewer_keywords:
- IDebugEngine2::CauseBreak
ms.assetid: 17fe4698-b04e-4798-8412-80e0da60c387
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 93f9937609a09439b265946e76f0af0381d488f1
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/29/2019
ms.locfileid: "66330134"
---
# <a name="idebugengine2causebreak"></a>IDebugEngine2::CauseBreak
Wszystkie programy, jest debugowane ten aparat debugowania (DE), aby zatrzymać wykonywanie podczas następnego żądania, jeden z wątków ich podejmie próbę uruchomienia.

## <a name="syntax"></a>Składnia

```cpp
HRESULT CauseBreak( 
   void 
);
```

```csharp
int CauseBreak();
```

## <a name="return-value"></a>Wartość zwracana
 Jeśli operacja się powiedzie, zwraca `S_OK`; w przeciwnym razie zwraca kod błędu.

## <a name="remarks"></a>Uwagi
 Ta metoda jest asynchroniczne: [IDebugBreakEvent2](../../../extensibility/debugger/reference/idebugbreakevent2.md) jest wysyłane zdarzenie, gdy program następnie próbuje wykonać po ta metoda jest wywoływana.

## <a name="see-also"></a>Zobacz także
- [CauseBreak](../../../extensibility/debugger/reference/idebugprogram2-causebreak.md)
- [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)