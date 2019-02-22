---
title: IDebugMethodField::EnumLocals | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugMethodField::EnumLocals
helpviewer_keywords:
- IDebugMethodField::EnumLocals method
ms.assetid: b0456a6d-2b96-49e2-a871-516571b4f6a5
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 6e8c39adaca6c394b631542d57d74ed4818501b4
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/22/2019
ms.locfileid: "56700565"
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

#### <a name="parameters"></a>Parametry
`pAddress`

 [in] [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md) obiekt reprezentujący adres debugowania, który wybiera kontekst lub zakres, z którego mają zostać pobrane zmienne lokalne.

`ppLocals`

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

## <a name="see-also"></a>Zobacz też
- [IDebugMethodField](../../../extensibility/debugger/reference/idebugmethodfield.md)
- [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md)
- [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)
- [EnumAllLocals](../../../extensibility/debugger/reference/idebugmethodfield-enumalllocals.md)
