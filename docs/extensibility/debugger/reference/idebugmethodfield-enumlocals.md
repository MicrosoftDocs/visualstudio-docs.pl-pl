---
title: 'IDebugMethodField:: EnumLocals | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugMethodField::EnumLocals
helpviewer_keywords:
- IDebugMethodField::EnumLocals method
ms.assetid: b0456a6d-2b96-49e2-a871-516571b4f6a5
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 98d6d7c4d9f1df0c7c4346792d841de574859619
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99861156"
---
# <a name="idebugmethodfieldenumlocals"></a>IDebugMethodField::EnumLocals
Tworzy moduł wyliczający dla wybranych zmiennych lokalnych metody.

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
podczas Obiekt [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md) reprezentujący adres debugowania, który wybiera kontekst lub zakres, z którego mają zostać pobrane elementy lokalne.

`ppLocals`\
określoną Zwraca obiekt [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md) reprezentujący listę wartości lokalnych; w przeciwnym razie zwraca wartość null, jeśli nie ma żadnych wartości lokalnych.

## <a name="return-value"></a>Wartość zwracana
Jeśli to się powiedzie, zwraca S_OK lub zwraca S_FALSE, jeśli nie ma żadnych ustawień lokalnych. W przeciwnym razie zwraca kod błędu.

## <a name="remarks"></a>Uwagi
Wyliczane są tylko zmienne zdefiniowane w bloku, który zawiera dany adres debugowania. Jeśli potrzebne są wszystkie elementy lokalne, w tym wszystkie elementy lokalne generowane przez kompilator, należy wywołać metodę [EnumAllLocals](../../../extensibility/debugger/reference/idebugmethodfield-enumalllocals.md) .

Metoda może zawierać wiele kontekstów lub bloków określania zakresu. Na przykład następująca metoda contrived zawiera trzy zakresy, dwa wewnętrzne bloki i treść metody.

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

Obiekt [IDebugMethodField](../../../extensibility/debugger/reference/idebugmethodfield.md) reprezentuje `func` samą metodę. Wywołanie `EnumLocals` metody z [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md) ustawionym na `Inner Scope 1` adres zwraca Wyliczenie zawierające `temp1` zmienną, na przykład.

## <a name="see-also"></a>Zobacz też
- [IDebugMethodField](../../../extensibility/debugger/reference/idebugmethodfield.md)
- [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md)
- [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)
- [EnumAllLocals](../../../extensibility/debugger/reference/idebugmethodfield-enumalllocals.md)
