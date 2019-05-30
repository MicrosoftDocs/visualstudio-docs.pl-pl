---
title: IDebugMethodField::EnumLocals | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugMethodField::EnumLocals
helpviewer_keywords:
- IDebugMethodField::EnumLocals method
ms.assetid: b0456a6d-2b96-49e2-a871-516571b4f6a5
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: bd4e2ffcaa66af58d3cc7ab57420de32d77eec92
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/29/2019
ms.locfileid: "66346773"
---
# <a name="idebugmethodfieldenumlocals"></a>IDebugMethodField::EnumLocals
Tworzy moduł wyliczający wybrane zmienne lokalne, metody.

## <a name="syntax"></a>Składnia

```cpp
HRESULT EnumLocals(
    IDebugAddress*     pAddress,
    IEnumDebugFields** ppLocals
);
```

```csharp
int EnumLocals(
    IDebugAddress        pAddress,
    out IEnumDebugFields ppLocals
);
```

## <a name="parameters"></a>Parametry
`pAddress`\
[in] [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md) obiekt reprezentujący adres debugowania, który wybiera kontekst lub zakres, z którego mają zostać pobrane zmienne lokalne.

`ppLocals`\
[out] Zwraca [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md) obiekt reprezentujący listę zmienne; w przeciwnym razie zwraca wartość null, jeśli nie ma żadnych zmiennych lokalnych.

## <a name="return-value"></a>Wartość zwracana
Jeśli to się powiedzie, zwraca wartość S_OK lub zwraca wartość S_FALSE, jeśli nie ma żadnych zmiennych lokalnych. W przeciwnym razie zwraca kod błędu.

## <a name="remarks"></a>Uwagi
Wyliczane są tylko zmienne zdefiniowane w obrębie bloku, który zawiera adres danego debugowania. Jeśli potrzebne są wszystkie zmienne lokalne, w tym elementy lokalne generowanych przez kompilator, wywołaj [EnumAllLocals](../../../extensibility/debugger/reference/idebugmethodfield-enumalllocals.md) metody.

Metoda może zawierać wielu kontekstach lub bloków zakresu. Na przykład następującą metodę contrived zawiera trzy zakresy, dwóch bloków wewnętrzny i treści metody, sam.

```csharp
public void func(int index)
{
    // Method body scope
    int a = 0;
    if (index == 1)
    {
        // Inner scope 1
        int temp1 = a;
    }
    else
    {
        // Inner scope 2
        int temp2 = a;
    }
}
```

[IDebugMethodField](../../../extensibility/debugger/reference/idebugmethodfield.md) obiekt reprezentuje `func` sama metoda. Wywoływanie `EnumLocals` metody z [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md) równa `Inner Scope 1` adres zwraca wyliczenie zawierający `temp1` zmiennej, na przykład.

## <a name="see-also"></a>Zobacz także
- [IDebugMethodField](../../../extensibility/debugger/reference/idebugmethodfield.md)
- [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md)
- [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)
- [EnumAllLocals](../../../extensibility/debugger/reference/idebugmethodfield-enumalllocals.md)
