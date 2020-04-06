---
title: IDebugThread2::GetName | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugThread2::GetName
helpviewer_keywords:
- IDebugThread2::GetName
ms.assetid: eec54b8f-4a0e-4919-b0f9-81d4bd1e0b6f
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 9d4828b573585969154f2ad1d484c9fcdf767417
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80718774"
---
# <a name="idebugthread2getname"></a>IDebugThread2::GetName
Pobiera nazwę wątku.

## <a name="syntax"></a>Składnia

```cpp
HRESULT GetName ( 
   BSTR* pbstrName
);
```

```csharp
int GetName ( 
   out string pbstrName
);
```

## <a name="parameters"></a>Parametry
`pbstrName`\
[na zewnątrz] Zwraca nazwę wątku.

## <a name="return-value"></a>Wartość zwracana
 Jeśli się `S_OK`powiedzie, zwraca ; w przeciwnym razie zwraca kod błędu.

## <a name="remarks"></a>Uwagi
 Pobrana nazwa jest zawsze nazwą, która może być wyświetlana i ta nazwa opisuje wątek. Nazwa wątku może pochodzić z architektury w czasie wykonywania, która obsługuje nazwane wątki lub może to być nazwa pochodząca z aparatu debugowania. Alternatywnie nazwa wątku można ustawić przez wywołanie [SetThreadName](../../../extensibility/debugger/reference/idebugthread2-setthreadname.md) metody.

## <a name="see-also"></a>Zobacz też
- [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)
- [SetThreadName](../../../extensibility/debugger/reference/idebugthread2-setthreadname.md)
