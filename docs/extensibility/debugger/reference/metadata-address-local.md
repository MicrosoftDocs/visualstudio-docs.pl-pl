---
title: METADATA_ADDRESS_LOCAL | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- METADATA_ADDRESS_LOCAL
helpviewer_keywords:
- METADATA_ADDRESS_LOCAL structure
ms.assetid: 635f6bc5-c486-4e0e-83db-36f15e543843
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: f8500d7ad1e03e08fa852afe9b8b77e49562f355
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/29/2019
ms.locfileid: "66345632"
---
# <a name="metadataaddresslocal"></a>METADATA_ADDRESS_LOCAL

Ta struktura reprezentuje adres zmiennej lokalnej w zakresie (zazwyczaj funkcja lub metoda).

## <a name="syntax"></a>Składnia

```cpp
typedef struct _tagMETADATA_ADDRESS_LOCAL {
    _mdToken  tokMethod;
    IUnknown* pLocal;
    DWORD     dwIndex;
} METADATA_ADDRESS_LOCAL;
```

```csharp
public struct METADATA_ADDRESS_LOCAL {
    public int    tokMethod;
    public object pLocal;
    public uint   dwIndex;
}
```

## <a name="members"></a>Elementy członkowskie

`tokMethod`\
ID metody lub funkcji zmiennej lokalnej jest częścią.

[C++] `_mdToken` jest `typedef` dla 32-bitowych `int`.

`pLocal`\
Token, którego adres przedstawia tę strukturę.

`dwIndex`\
Może być indeksem tej zmiennej lokalnej w metody lub funkcji lub inną wartość (specyficzne dla języka).

## <a name="remarks"></a>Uwagi

Ta struktura jest częścią Unii w [DEBUG_ADDRESS_UNION](../../../extensibility/debugger/reference/debug-address-union.md) struktury, kiedy `dwKind` pole `DEBUG_ADDRESS_UNION` struktury jest ustawiona na `ADDRESS_KIND_LOCAL` (wartość z zakresu od [ADDRESS_KIND](../../../extensibility/debugger/reference/address-kind.md) Wyliczenie).

> [!WARNING]
> [C++ tylko] Jeśli `pLocal` ma wartość null, nie należy wywołać `Release` tokenu wskaźnika (`addr` jest polem w [DEBUG_ADDRESS](../../../extensibility/debugger/reference/debug-address.md) struktury):
>
> ```cpp
> if (addr.dwKind == ADDRESS_KIND_METADATA_LOCAL && addr.addr.addrLocal.pLocal != NULL)
> {
>     addr.addr.addrLocal.pLocal->Release();
> }
> ```

## <a name="requirements"></a>Wymagania

Nagłówek: sh.h

Przestrzeń nazw: Microsoft.VisualStudio.Debugger.Interop

Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Zobacz także

- [Struktury i związki](../../../extensibility/debugger/reference/structures-and-unions.md)
- [DEBUG_ADDRESS_UNION](../../../extensibility/debugger/reference/debug-address-union.md)
- [DEBUG_ADDRESS](../../../extensibility/debugger/reference/debug-address.md)
- [ADDRESS_KIND](../../../extensibility/debugger/reference/address-kind.md)
