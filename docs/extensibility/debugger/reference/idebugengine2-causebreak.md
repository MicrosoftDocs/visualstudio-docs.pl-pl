---
title: 'IDebugEngine2:: CauseBreak | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEngine2::CauseBreak
helpviewer_keywords:
- IDebugEngine2::CauseBreak
ms.assetid: 17fe4698-b04e-4798-8412-80e0da60c387
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: b40fd243fa8f3f67786b862c3e0cdbfd81373a53
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99899017"
---
# <a name="idebugengine2causebreak"></a>IDebugEngine2::CauseBreak
Żądania, które wszystkie programy są debugowane przez ten aparat debugowania (DE), aby zatrzymać wykonywanie przy następnym uruchomieniu jednego z ich wątków.

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
 Jeśli powiedzie się, zwraca `S_OK` ; w przeciwnym razie zwraca kod błędu.

## <a name="remarks"></a>Uwagi
 Ta metoda jest asynchroniczna: zdarzenie [IDebugBreakEvent2](../../../extensibility/debugger/reference/idebugbreakevent2.md) jest wysyłane, gdy program próbuje wykonać operację po wywołaniu tej metody.

## <a name="see-also"></a>Zobacz też
- [CauseBreak](../../../extensibility/debugger/reference/idebugprogram2-causebreak.md)
- [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)
