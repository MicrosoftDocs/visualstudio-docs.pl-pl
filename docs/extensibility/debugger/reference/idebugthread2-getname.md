---
title: 'IDebugThread2:: GetName | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugThread2::GetName
helpviewer_keywords:
- IDebugThread2::GetName
ms.assetid: eec54b8f-4a0e-4919-b0f9-81d4bd1e0b6f
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 7a8a7a4f041e2a38cf1e24e8cf156d3e595010b6
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99893857"
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
określoną Zwraca nazwę wątku.

## <a name="return-value"></a>Wartość zwracana
 Jeśli powiedzie się, zwraca `S_OK` ; w przeciwnym razie zwraca kod błędu.

## <a name="remarks"></a>Uwagi
 Pobrana nazwa jest zawsze nazwą, którą można wyświetlić, a ta nazwa opisuje wątek. Nazwa wątku może być pochodną architektury czasu wykonywania, która obsługuje nazwane wątki, lub może być nazwą pochodną aparatu debugowania. Alternatywnie można ustawić nazwę wątku za pomocą wywołania metody [SetThreadName](../../../extensibility/debugger/reference/idebugthread2-setthreadname.md) .

## <a name="see-also"></a>Zobacz też
- [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)
- [SetThreadName](../../../extensibility/debugger/reference/idebugthread2-setthreadname.md)
