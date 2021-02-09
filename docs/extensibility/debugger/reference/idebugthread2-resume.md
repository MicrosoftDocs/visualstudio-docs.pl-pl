---
title: 'IDebugThread2:: Resume | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugThread2::Resume
helpviewer_keywords:
- IDebugThread2::Resume
ms.assetid: 36aad682-b0b9-40a2-b3fc-f0e61d41cdbc
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 6156becc782adb054af37cf24efd64915729149c
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99893727"
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
określoną Zwraca liczbę wstrzymań po operacji wznawiania.

## <a name="return-value"></a>Wartość zwracana
 Jeśli powiedzie się, zwraca `S_OK` ; w przeciwnym razie zwraca kod błędu.

## <a name="remarks"></a>Uwagi
 Każde wywołanie tej metody zmniejsza liczbę wstrzymania do momentu, aż osiągnie wartość 0, a wykonanie jest ostatecznie wznawiane. Ta liczba wstrzymań zostanie wyświetlona w oknie Debugowanie **wątków** .

 Dla każdego wywołania tej metody musi istnieć poprzednie wywołanie metody [Suspend](../../../extensibility/debugger/reference/idebugthread2-suspend.md) . Liczba wstrzymań określa, ile razy Metoda została wywołana do tej `IDebugThread2::Suspend` pory.

## <a name="see-also"></a>Zobacz też
- [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)
- [Wstrzymanie](../../../extensibility/debugger/reference/idebugthread2-suspend.md)
