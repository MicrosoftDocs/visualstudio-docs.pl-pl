---
title: METADATA_ADDRESS_LOCAL | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- METADATA_ADDRESS_LOCAL
helpviewer_keywords:
- METADATA_ADDRESS_LOCAL structure
ms.assetid: 635f6bc5-c486-4e0e-83db-36f15e543843
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: e3adf9ca5f679c7a526f10b1ee6c91d50dac52d2
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80714476"
---
# <a name="metadata_address_local"></a>METADATA_ADDRESS_LOCAL

Ta struktura reprezentuje adres zmiennej lokalnej w zakresie (zwykle funkcji lub metody).

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
Identyfikator metody lub funkcji zmiennej lokalnej jest częścią.

[C++] `_mdToken` jest `typedef` dla 32-bitowego `int`.

`pLocal`\
Token, którego adres reprezentuje ta struktura.

`dwIndex`\
Może to być indeks tej zmiennej lokalnej w metodzie lub funkcji lub inną wartość (specyficzne dla języka).

## <a name="remarks"></a>Uwagi

Ta struktura jest częścią unii w [strukturze DEBUG_ADDRESS_UNION,](../../../extensibility/debugger/reference/debug-address-union.md) `dwKind` gdy `DEBUG_ADDRESS_UNION` pole struktury `ADDRESS_KIND_LOCAL` jest ustawiona na (wartość z [ADDRESS_KIND](../../../extensibility/debugger/reference/address-kind.md) wyliczenia).

> [!WARNING]
> [Tylko C++] Jeśli `pLocal` nie ma wartości null, należy wywołać `Release` wskaźnik tokenu (`addr` jest polem w strukturze [DEBUG_ADDRESS):](../../../extensibility/debugger/reference/debug-address.md)
>
> ```cpp
> if (addr.dwKind == ADDRESS_KIND_METADATA_LOCAL && addr.addr.addrLocal.pLocal != NULL)
> {
>     addr.addr.addrLocal.pLocal->Release();
> }
> ```

## <a name="requirements"></a>Wymagania

Nagłówek: sh.h

Obszar nazw: Microsoft.VisualStudio.Debugger.Interop

Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Zobacz też

- [Struktury i związki](../../../extensibility/debugger/reference/structures-and-unions.md)
- [DEBUG_ADDRESS_UNION](../../../extensibility/debugger/reference/debug-address-union.md)
- [DEBUG_ADDRESS](../../../extensibility/debugger/reference/debug-address.md)
- [ADDRESS_KIND](../../../extensibility/debugger/reference/address-kind.md)
