---
title: IDebugThread2::Zawiesić | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugThread2::Suspend
helpviewer_keywords:
- IDebugThread2::Suspend
ms.assetid: 1e20be85-aa12-48de-bb83-0bf0976e99ae
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 74a7dd5dc69effbd46986eff963de3e740d9aa8e
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80718638"
---
# <a name="idebugthread2suspend"></a>IDebugThread2::Suspend
Zawiesza wątek.

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
[na zewnątrz] Zwraca liczbę wstrzymań po operacji wstrzymania.

## <a name="return-value"></a>Wartość zwracana
 Jeśli się `S_OK`powiedzie, zwraca ; w przeciwnym razie zwraca kod błędu.

## <a name="remarks"></a>Uwagi
 Każde wywołanie tej metody zwiększa liczbę wstrzymania powyżej 0. Ta liczba wstrzymania jest wyświetlana w oknie debugowania **wątków.**

 Dla każdego wywołania tej metody musi być późniejsze wywołanie [metody Resume.](../../../extensibility/debugger/reference/idebugthread2-resume.md)

## <a name="see-also"></a>Zobacz też
- [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)
- [Resume](../../../extensibility/debugger/reference/idebugthread2-resume.md)
