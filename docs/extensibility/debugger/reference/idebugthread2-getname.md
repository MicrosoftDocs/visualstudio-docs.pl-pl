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
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 9d4828b573585969154f2ad1d484c9fcdf767417
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
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
określoną Zwraca nazwę wątku.

## <a name="return-value"></a>Wartość zwracana
 Jeśli powiedzie się, zwraca `S_OK` ; w przeciwnym razie zwraca kod błędu.

## <a name="remarks"></a>Uwagi
 Pobrana nazwa jest zawsze nazwą, którą można wyświetlić, a ta nazwa opisuje wątek. Nazwa wątku może być pochodną architektury czasu wykonywania, która obsługuje nazwane wątki, lub może być nazwą pochodną aparatu debugowania. Alternatywnie można ustawić nazwę wątku za pomocą wywołania metody [SetThreadName](../../../extensibility/debugger/reference/idebugthread2-setthreadname.md) .

## <a name="see-also"></a>Zobacz też
- [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)
- [SetThreadName](../../../extensibility/debugger/reference/idebugthread2-setthreadname.md)
