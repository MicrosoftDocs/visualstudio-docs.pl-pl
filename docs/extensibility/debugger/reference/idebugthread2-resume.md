---
title: IDebugThread2::Wznów | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugThread2::Resume
helpviewer_keywords:
- IDebugThread2::Resume
ms.assetid: 36aad682-b0b9-40a2-b3fc-f0e61d41cdbc
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 3899dea7c33946588de4308f42b948ede703361a
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80718673"
---
# <a name="idebugthread2resume"></a>IDebugThread2::Resume
Wznawia wykonywanie wątku.

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
[na zewnątrz] Zwraca liczbę wstrzymań po operacji wznowienia.

## <a name="return-value"></a>Wartość zwracana
 Jeśli się `S_OK`powiedzie, zwraca ; w przeciwnym razie zwraca kod błędu.

## <a name="remarks"></a>Uwagi
 Każde wywołanie tej metody zmniejsza liczbę wstrzymania, dopóki nie osiągnie 0, w którym czasie wykonanie jest faktycznie wznowione. Ta liczba wstrzymania jest wyświetlana w oknie debugowania **wątków.**

 Dla każdego wywołania tej metody musi być poprzednie [wywołanie Suspend](../../../extensibility/debugger/reference/idebugthread2-suspend.md) metody. Liczba wstrzymania określa, ile `IDebugThread2::Suspend` razy metoda została wywołana do tej pory.

## <a name="see-also"></a>Zobacz też
- [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)
- [Suspend](../../../extensibility/debugger/reference/idebugthread2-suspend.md)
