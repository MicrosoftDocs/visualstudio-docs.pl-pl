---
title: IDebugProgram2::GetMemoryBytes | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgram2::GetMemoryBytes
helpviewer_keywords:
- IDebugProgram2::GetMemoryBytes
ms.assetid: 1cdedb47-caf8-468e-aaf4-163f16afb403
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: ca06bd4593401544155e53c21315499d85edc07a
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/29/2019
ms.locfileid: "66319434"
---
# <a name="idebugprogram2getmemorybytes"></a>IDebugProgram2::GetMemoryBytes
Pobiera bajtów pamięci zajmowane przez program.

## <a name="syntax"></a>Składnia

```cpp
HRESULT GetMemoryBytes( 
   IDebugMemoryBytes2** ppMemoryBytes
);
```

```csharp
int GetMemoryBytes( 
   out IDebugMemoryBytes2 ppMemoryBytes
);
```

## <a name="parameters"></a>Parametry
`ppMemoryBytes`\
[out] Zwraca [IDebugMemoryBytes2](../../../extensibility/debugger/reference/idebugmemorybytes2.md) obiekt, który reprezentuje bajtów pamięci programu.

## <a name="return-value"></a>Wartość zwracana
 Jeśli operacja się powiedzie, zwraca `S_OK`; w przeciwnym razie zwraca kod błędu.

## <a name="remarks"></a>Uwagi
 Bajty pamięci, reprezentowane przez [IDebugMemoryBytes2](../../../extensibility/debugger/reference/idebugmemorybytes2.md) obiektów jest przeznaczony dla programu obrazu w pamięci i nie wszystkie pamięci, która została przydzielona, gdy program został wykonany.

## <a name="see-also"></a>Zobacz także
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
- [IDebugMemoryBytes2](../../../extensibility/debugger/reference/idebugmemorybytes2.md)