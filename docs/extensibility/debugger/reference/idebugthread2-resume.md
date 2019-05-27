---
title: IDebugThread2::Resume | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugThread2::Resume
helpviewer_keywords:
- IDebugThread2::Resume
ms.assetid: 36aad682-b0b9-40a2-b3fc-f0e61d41cdbc
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 3b96ddd99c2d3377a5c48bb40660e17671ded0ca
ms.sourcegitcommit: 19ec963ed6d585719cb83ba677434ea6580e0d1f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/24/2019
ms.locfileid: "66199527"
---
# <a name="idebugthread2resume"></a>IDebugThread2::Resume
Wznawia wykonanie wątku.

## <a name="syntax"></a>Składnia

```cpp
HRESULT Resume ( 
   DWORD *pdwSuspendCount
);
```

```csharp
int Resume ( 
   out uint pdwSuspendCount
);
```

## <a name="parameters"></a>Parametry
`pdwSuspendCount`\
[out] Zwraca wstrzymania liczenia przez operację wznawiania.

## <a name="return-value"></a>Wartość zwracana
 Jeśli operacja się powiedzie, zwraca `S_OK`; w przeciwnym razie zwraca kod błędu.

## <a name="remarks"></a>Uwagi
 Każdy wywołanie tej metody zmniejsza wstrzymania liczenia aż do napotkania 0 w tym czasie faktycznie wznowiono wykonywanie. Ten licznik Wstrzymaj jest wyświetlana w **wątków** okna debugowania.

 Dla każdego wywołania tej metody musi być poprzednie wywołanie [Wstrzymaj](../../../extensibility/debugger/reference/idebugthread2-suspend.md) metody. Wstrzymania liczenia Określa, ile razy `IDebugThread2::Suspend` do tej pory została wywołana metoda.

## <a name="see-also"></a>Zobacz także
- [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)
- [Suspend](../../../extensibility/debugger/reference/idebugthread2-suspend.md)