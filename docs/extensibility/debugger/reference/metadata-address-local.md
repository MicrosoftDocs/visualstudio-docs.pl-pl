---
title: METADATA_ADDRESS_LOCAL | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- METADATA_ADDRESS_LOCAL
helpviewer_keywords:
- METADATA_ADDRESS_LOCAL structure
ms.assetid: 635f6bc5-c486-4e0e-83db-36f15e543843
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 8ac19a3e59e70d0a1fb03b78e64036bd2ac23219
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62865839"
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

## <a name="terms"></a>Warunki

`tokMethod`

ID metody lub funkcji zmiennej lokalnej jest częścią.

[C++] `_mdToken` jest `typedef` dla 32-bitowych `int`.

`pLocal`

Token, którego adres przedstawia tę strukturę.

`dwIndex`

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
