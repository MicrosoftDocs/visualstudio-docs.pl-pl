---
title: IDebugMemoryContext2::Subtract | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugMemoryContext2::Subtract
helpviewer_keywords:
- Subtract method
- IDebugMemoryContext2::Subtract method
ms.assetid: 63df14c7-8d7e-47c1-afa7-5a1ab5d8eaba
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: a320b7c67cd2603dfea11983d2d62c344f347ab4
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/29/2019
ms.locfileid: "66347018"
---
# <a name="idebugmemorycontext2subtract"></a>IDebugMemoryContext2::Subtract
Odejmuje określoną wartość z bieżącego kontekstu i zwraca nowy kontekst.

## <a name="syntax"></a>Składnia

```cpp
HRESULT Subtract( 
   UINT64                 dwCount,
   IDebugMemoryContext2** ppMemCxt
);
```

```csharp
int Subtract(
   ulong                    dwCount,
   out IDebugMemoryContext2 ppMemCxt
);
```

## <a name="parameters"></a>Parametry
`dwCount`\
[in] Liczba bajtów pamięci, aby zmniejszyć.

`ppMemCxt`\
[out] Zwraca nowy [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md) obiektu.

## <a name="return-value"></a>Wartość zwracana
 Jeśli operacja się powiedzie, zwraca `S_OK`; w przeciwnym razie zwraca kod błędu.

## <a name="remarks"></a>Uwagi
 Kontekst pamięci nie jest adresem, więc odjęcie wartości z adresu tworzy nowy adres, który wymaga nowy interfejs kontekstu.

 Ta metoda zawsze musi mieć nowy kontekst, nawet jeśli otrzymany adres znajduje się poza obszar pamięci skojarzone z tym kontekstem. Jedynym wyjątkiem jest, jeśli nie pamięć może być przydzielenia w nowym kontekście lub `ppMemCxt` jest wartością null (jest to błąd).

## <a name="see-also"></a>Zobacz także
- [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md)