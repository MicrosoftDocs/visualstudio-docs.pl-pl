---
title: IDebugThread2::Suspend | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugThread2::Suspend
helpviewer_keywords:
- IDebugThread2::Suspend
ms.assetid: 1e20be85-aa12-48de-bb83-0bf0976e99ae
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: dc3abcc00d99e82a4af2e3886310772e47127274
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/29/2019
ms.locfileid: "66320012"
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