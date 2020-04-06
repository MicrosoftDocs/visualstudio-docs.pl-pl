---
title: DEBUG_ADDRESS | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- DEBUG_ADDRESS
helpviewer_keywords:
- DEBUG_ADDRESS structure
ms.assetid: 79f5e765-9aac-4b6e-82ef-bed88095e9ba
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: fe778ba3ed80930a4cd7b4fa1170f286b3ccf6ec
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80737511"
---
# <a name="debug_address"></a>DEBUG_ADDRESS
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

## <a name="members"></a>Elementy członkowskie
`ulAppDomainID`\
Identyfikator procesu.

`guidModule`\
Identyfikator GUID modułu zawierającego ten adres.

`tokClass`\
Token identyfikujący klasę lub typ tego adresu.

> [!NOTE]
> Ta wartość jest specyficzna dla dostawcy symbolu i dlatego nie ma ogólnego znaczenia innego niż jako identyfikator dla typu klasy.

`addr`\
Struktura [DEBUG_ADDRESS_UNION,](../../../extensibility/debugger/reference/debug-address-union.md) która zawiera unię struktur opisujących poszczególne typy adresów. Wartość `addr`.`dwKind` pochodzi z wyliczenia [ADDRESS_KIND,](../../../extensibility/debugger/reference/address-kind.md) które wyjaśnia, jak interpretować związek.

## <a name="remarks"></a>Uwagi
Ta struktura jest przekazywana do [GetAddress](../../../extensibility/debugger/reference/idebugaddress-getaddress.md) metody do wypełnienia.

**Ostrzeżenie [Tylko C++]**

Jeśli `addr.dwKind` `ADDRESS_KIND_METADATA_LOCAL` jest, `addr.addr.addrLocal.pLocal` a jeśli nie jest wartością null, należy wywołać `Release` wskaźnik tokenu:

```
if (addr.dwKind == ADDRESS_KIND_METADATA_LOCAL && addr.addr.addrLocal.pLocal != NULL)
{
    addr.addr.addrLocal.pLocal->Release();
}
```

## <a name="requirements"></a>Wymagania
Nagłówek: sh.h

Obszar nazw: Microsoft.VisualStudio.Debugger.Interop

Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Zobacz też
- [Struktury i związki](../../../extensibility/debugger/reference/structures-and-unions.md)
- [GetAddress](../../../extensibility/debugger/reference/idebugaddress-getaddress.md)
- [DEBUG_ADDRESS_UNION](../../../extensibility/debugger/reference/debug-address-union.md)
- [ADDRESS_KIND](../../../extensibility/debugger/reference/address-kind.md)
