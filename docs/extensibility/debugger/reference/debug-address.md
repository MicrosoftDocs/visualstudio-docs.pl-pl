---
title: DEBUG_ADDRESS | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- DEBUG_ADDRESS
helpviewer_keywords:
- DEBUG_ADDRESS structure
ms.assetid: 79f5e765-9aac-4b6e-82ef-bed88095e9ba
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: d45fa0be28fcad891366581e13425d3940a0a967
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62878075"
---
# <a name="debugaddress"></a>DEBUG_ADDRESS
Ta struktura reprezentuje adres.

## <a name="syntax"></a>Składnia

```cpp
typedef struct _tagDEBUG_ADDRESS {
    ULONG32             ulAppDomainID;
    GUID                guidModule;
    _mdToken            tokClass;
    DEBUG_ADDRESS_UNION addr;
} DEBUG_ADDRESS;
```

```csharp
public struct DEBUG_ADDRESS {
    public uint                ulAppDomainID;
    public Guid                guidModule;
    public int                 tokClass;
    public DEBUG_ADDRESS_UNION addr;
}
```

## <a name="terms"></a>Warunki
ulAppDomainID The process ID.

guidModule identyfikator GUID modułu, który zawiera ten adres.

tokClass token identyfikowanie klasy lub typ tego adresu.

> [!NOTE]
> Ta wartość jest specyficzne dla dostawcy symboli i dlatego nie ma znaczenia ogólne innych niż jako identyfikator dla typu klasy.

addr A [DEBUG_ADDRESS_UNION](../../../extensibility/debugger/reference/debug-address-union.md) struktury, która zawiera sumę struktur, które opisują typy poszczególnych adresów. Wartość `addr`.`dwKind` pochodzi z [ADDRESS_KIND](../../../extensibility/debugger/reference/address-kind.md) wyliczenia, w którym wyjaśniono, jak interpretować Unii.

## <a name="remarks"></a>Uwagi
Ta struktura jest przekazywany do [getaddress —](../../../extensibility/debugger/reference/idebugaddress-getaddress.md) metodę, aby wypełnić.

**Ostrzeżenie [C++ tylko]**

Jeśli `addr.dwKind` jest `ADDRESS_KIND_METADATA_LOCAL` i, jeśli `addr.addr.addrLocal.pLocal` nie jest wartością null, a następnie należy wywołać `Release` tokenu wskaźnika:

```
if (addr.dwKind == ADDRESS_KIND_METADATA_LOCAL && addr.addr.addrLocal.pLocal != NULL)
{
    addr.addr.addrLocal.pLocal->Release();
}
```

## <a name="requirements"></a>Wymagania
Nagłówek: sh.h

Przestrzeń nazw: Microsoft.VisualStudio.Debugger.Interop

Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Zobacz też
- [Struktury i związki](../../../extensibility/debugger/reference/structures-and-unions.md)
- [GetAddress](../../../extensibility/debugger/reference/idebugaddress-getaddress.md)
- [DEBUG_ADDRESS_UNION](../../../extensibility/debugger/reference/debug-address-union.md)
- [ADDRESS_KIND](../../../extensibility/debugger/reference/address-kind.md)
