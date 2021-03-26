---
description: Wstrzymuje wątek.
title: 'IDebugThread2:: Suspend | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugThread2::Suspend
helpviewer_keywords:
- IDebugThread2::Suspend
ms.assetid: 1e20be85-aa12-48de-bb83-0bf0976e99ae
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 902418aeb18c149b0732e972a34ed89b56bb22ce
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/25/2021
ms.locfileid: "105081142"
---
# <a name="idebugthread2suspend"></a>IDebugThread2::Suspend
Wstrzymuje wątek.

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
określoną Zwraca liczbę wstrzymań po operacji wstrzymywania.

## <a name="return-value"></a>Wartość zwracana
 Jeśli powiedzie się, zwraca `S_OK` ; w przeciwnym razie zwraca kod błędu.

## <a name="remarks"></a>Uwagi
 Każde wywołanie tej metody zwiększa liczbę wstrzymań powyżej 0. Ta liczba wstrzymań zostanie wyświetlona w oknie Debugowanie **wątków** .

 Dla każdego wywołania tej metody musi istnieć późniejsze wywołanie metody [Resume](../../../extensibility/debugger/reference/idebugthread2-resume.md) .

## <a name="see-also"></a>Zobacz też
- [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)
- [Wznawianie](../../../extensibility/debugger/reference/idebugthread2-resume.md)
