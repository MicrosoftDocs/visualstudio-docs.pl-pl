---
title: DEBUG_ADDRESS | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
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
ms.openlocfilehash: 779564cf93e22f64b926a80644bb9da3375335b9
ms.sourcegitcommit: 752f03977f45169585e407ef719450dbe219b7fc
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/15/2019
ms.locfileid: "56317825"
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
ulAppDomainID  
Identyfikator procesu.

guidModule  
Identyfikator GUID moduł, który zawiera ten adres.

tokClass  
Token, który identyfikuje klasy lub typ tego adresu.

> [!NOTE]
> Ta wartość jest specyficzne dla dostawcy symboli i dlatego nie ma znaczenia ogólne innych niż jako identyfikator dla typu klasy.

addr A [DEBUG_ADDRESS_UNION](../../../extensibility/debugger/reference/debug-address-union.md) struktury, która zawiera sumę struktur, które opisują typy poszczególnych adresów. Wartość `addr`.`dwKind` pochodzi z [ADDRESS_KIND](../../../extensibility/debugger/reference/address-kind.md) wyliczenia, w którym wyjaśniono, jak interpretować Unii.

## <a name="remarks"></a>Uwagi
Ta struktura jest przekazywany do [getaddress —](../../../extensibility/debugger/reference/idebugaddress-getaddress.md) metodę, aby wypełnić.

**Ostrzeżenie [tylko w języku C++]**

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
[Struktury i związki](../../../extensibility/debugger/reference/structures-and-unions.md)  
[GetAddress](../../../extensibility/debugger/reference/idebugaddress-getaddress.md)  
[DEBUG_ADDRESS_UNION](../../../extensibility/debugger/reference/debug-address-union.md)  
[ADDRESS_KIND](../../../extensibility/debugger/reference/address-kind.md)
