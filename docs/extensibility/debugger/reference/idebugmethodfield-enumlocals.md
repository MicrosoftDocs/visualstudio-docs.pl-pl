---
title: IDebugMethodField::EnumLocals | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugMethodField::EnumLocals
helpviewer_keywords:
- IDebugMethodField::EnumLocals method
ms.assetid: b0456a6d-2b96-49e2-a871-516571b4f6a5
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 08872160860d0d442f9807705dea70190dff9b28
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80727204"
---
# <a name="idebugmethodfieldenumlocals"></a>IDebugMethodField::EnumLocals
Tworzy wyliczyć dla wybranych zmiennych lokalnych metody.

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
[w] [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md) obiektu reprezentującego adres debugowania, który wybiera kontekst lub zakres, z którego można uzyskać lokalnych.

`ppLocals`\
[na zewnątrz] Zwraca [obiekt IEnumDebugFields reprezentujący](../../../extensibility/debugger/reference/ienumdebugfields.md) listę lokalnych mieszkańców; w przeciwnym razie zwraca wartość null, jeśli nie ma żadnych lokalnych.

## <a name="return-value"></a>Wartość zwracana
Jeśli się powiedzie, zwraca S_OK lub zwraca S_FALSE, jeśli nie ma mieszkańców. W przeciwnym razie zwraca kod błędu.

## <a name="remarks"></a>Uwagi
Wyliczano tylko zmienne zdefiniowane w bloku zawierającym podany adres debugowania. Jeśli wszystkie lokalne, w tym dowolnego lokalnego generowanego przez kompilatora są potrzebne, wywołaj [EnumAllLocals](../../../extensibility/debugger/reference/idebugmethodfield-enumalllocals.md) metody.

Metoda może zawierać wiele kontekstów zakresu lub bloków. Na przykład następująca wymyślona metoda zawiera trzy zakresy, dwa bloki wewnętrzne i samą treść metody.

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

[IDebugMethodField](../../../extensibility/debugger/reference/idebugmethodfield.md) obiekt reprezentuje `func` samą metodę. Wywołanie `EnumLocals` metody z [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md) `Inner Scope 1` zestaw do adresu zwraca wyliczenie zawierające zmienną, `temp1` na przykład.

## <a name="see-also"></a>Zobacz też
- [IDebugMethodField](../../../extensibility/debugger/reference/idebugmethodfield.md)
- [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md)
- [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)
- [EnumAllLocals](../../../extensibility/debugger/reference/idebugmethodfield-enumalllocals.md)
