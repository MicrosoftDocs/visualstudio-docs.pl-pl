---
title: IDebugMemoryContext2::GetName | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugMemoryContext2::GetName
helpviewer_keywords:
- IDebugMemoryContext2::GetName method
- GetName method
ms.assetid: 8c212556-7d9e-4d68-b2a9-8212f50d0287
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: ee8dd65a3bcaef7fd5a23da6c2a5f9c21a4838af
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/29/2019
ms.locfileid: "66346995"
---
# <a name="idebugmemorycontext2getname"></a>IDebugMemoryContext2::GetName
Pobiera użytkownika zawiera nazwę dla tego kontekstu.

## <a name="syntax"></a>Składnia

```cpp
HRESULT GetName( 
   BSTR* pbstrName
);
```

```csharp
int GetName(
   out string pbstrName
);
```

## <a name="parameters"></a>Parametry
`pbstrName`\
[out] Zwraca nazwę kontekstu pamięci.

## <a name="return-value"></a>Wartość zwracana
 Jeśli operacja się powiedzie, zwraca `S_OK`; w przeciwnym razie zwraca kod błędu.

## <a name="remarks"></a>Uwagi
 Nazwa kontekstu pamięci nie jest zwykle używana.

## <a name="see-also"></a>Zobacz także
- [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md)