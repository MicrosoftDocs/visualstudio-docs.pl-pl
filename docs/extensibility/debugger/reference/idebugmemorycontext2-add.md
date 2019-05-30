---
title: IDebugMemoryContext2::Add | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugMemoryContext2::Add
helpviewer_keywords:
- IDebugMemoryContext2::Add method
- Add method
ms.assetid: 3c47e646-ce9e-4dd3-8f1a-6dbd3827d407
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: c1cafbf22e51f867948491e2925c085bd387ea84
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/29/2019
ms.locfileid: "66347090"
---
# <a name="idebugmemorycontext2add"></a>IDebugMemoryContext2::Add
Dodaje określoną wartość do bieżącego kontekstu i zwraca nowy kontekst.

## <a name="syntax"></a>Składnia

```cpp
HRESULT Add( 
   UINT64                 dwCount,
   IDebugMemoryContext2** ppMemCxt
);
```

```csharp
int Add(
   ulong                    dwCount,
   out IDebugMemoryContext2 ppMemCxt
);
```

## <a name="parameters"></a>Parametry
`dwCount`\
[in] Wartość do dodania do bieżącego kontekstu.

`ppMemCxt`\
[out] Zwraca nowy [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md) obiektu.

## <a name="return-value"></a>Wartość zwracana
 Jeśli operacja się powiedzie, zwraca `S_OK`; w przeciwnym razie zwraca kod błędu.

## <a name="remarks"></a>Uwagi
 Kontekst pamięci nie jest adresem, dlatego dodanie wartości do adresu tworzy nowy adres, który wymaga nowy interfejs kontekstu.

 Ta metoda zawsze musi mieć nowy kontekst, nawet jeśli otrzymany adres znajduje się poza obszar pamięci skojarzone z tym kontekstem. Jedynym wyjątkiem jest, jeśli nie pamięć może być przydzielenia w nowym kontekście lub `ppMemCxt` jest wartością null (jest to błąd).

## <a name="see-also"></a>Zobacz także
- [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md)