---
title: IDebugThread2::Suspend | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugThread2::Suspend
helpviewer_keywords:
- IDebugThread2::Suspend
ms.assetid: 1e20be85-aa12-48de-bb83-0bf0976e99ae
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: b9df2f37a6e8acb9f8e37d2fbd1a379bc4572b39
ms.sourcegitcommit: 19ec963ed6d585719cb83ba677434ea6580e0d1f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/24/2019
ms.locfileid: "66199462"
---
# <a name="idebugthread2suspend"></a>IDebugThread2::Suspend
Wstrzymuje działanie wątku.

## <a name="syntax"></a>Składnia

```cpp
HRESULT Suspend ( 
   DWORD *pdwSuspendCount
);
```

```csharp
HRESULT Suspend ( 
   out uint pdwSuspendCount
);
```

## <a name="parameters"></a>Parametry
`pdwSuspendCount`\
[out] Zwraca przez operację zawieszania wstrzymania liczenia.

## <a name="return-value"></a>Wartość zwracana
 Jeśli operacja się powiedzie, zwraca `S_OK`; w przeciwnym razie zwraca kod błędu.

## <a name="remarks"></a>Uwagi
 Każde wywołanie tej metody zwiększa liczbę Wstrzymaj powyżej 0. Ten licznik Wstrzymaj jest wyświetlana w **wątków** okna debugowania.

 Dla każdego wywołania tej metody musi być wywołaniem nowsze [Wznów](../../../extensibility/debugger/reference/idebugthread2-resume.md) metody.

## <a name="see-also"></a>Zobacz także
- [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)
- [Resume](../../../extensibility/debugger/reference/idebugthread2-resume.md)