---
title: 'IDebugThread2:: Suspend | Microsoft Docs'
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "80718638"
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
