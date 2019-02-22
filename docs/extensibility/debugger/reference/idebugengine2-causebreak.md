---
title: IDebugEngine2::CauseBreak | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEngine2::CauseBreak
helpviewer_keywords:
- IDebugEngine2::CauseBreak
ms.assetid: 17fe4698-b04e-4798-8412-80e0da60c387
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: fa0d559887019a697b820a5a6c91f80b78c6b713
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/22/2019
ms.locfileid: "56678140"
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

## <a name="see-also"></a>Zobacz też
- [CauseBreak](../../../extensibility/debugger/reference/idebugprogram2-causebreak.md)
- [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)