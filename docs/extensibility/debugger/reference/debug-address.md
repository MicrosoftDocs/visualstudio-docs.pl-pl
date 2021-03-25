---
description: Ta struktura reprezentuje adres.
title: DEBUG_ADDRESS | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- DEBUG_ADDRESS
helpviewer_keywords:
- DEBUG_ADDRESS structure
ms.assetid: 79f5e765-9aac-4b6e-82ef-bed88095e9ba
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 1b250654f45f18adcfd9c52a6047b2b8798be75b
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/25/2021
ms.locfileid: "105096372"
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
> Ta wartość jest specyficzna dla dostawcy symboli, dlatego nie ma ogólnego znaczenia innego niż identyfikator dla typu klasy.

`addr`\
Struktura [DEBUG_ADDRESS_UNION](../../../extensibility/debugger/reference/debug-address-union.md) , która zawiera Unię struktur, które opisują poszczególne typy adresów. Wartość `addr` .`dwKind` pochodzi z wyliczenia [ADDRESS_KIND](../../../extensibility/debugger/reference/address-kind.md) , w którym wyjaśniono, jak interpretować Unię.

## <a name="remarks"></a>Uwagi
Ta struktura jest przenoszona do metody [GetAddress](../../../extensibility/debugger/reference/idebugaddress-getaddress.md) do wypełnienia.

**Ostrzeżenie [tylko C++]**

Jeśli `addr.dwKind` jest `ADDRESS_KIND_METADATA_LOCAL` i jeśli `addr.addr.addrLocal.pLocal` nie jest wartością null, należy wywołać `Release` wskaźnik tokenu:

```
if (addr.dwKind == ADDRESS_KIND_METADATA_LOCAL && addr.addr.addrLocal.pLocal != NULL)
{
    addr.addr.addrLocal.pLocal->Release();
}
```

## <a name="requirements"></a>Wymagania
Nagłówek: sh. h

Przestrzeń nazw: Microsoft. VisualStudio. Debugger. Interop

Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Zobacz też
- [Struktury i związki](../../../extensibility/debugger/reference/structures-and-unions.md)
- [GetAddress](../../../extensibility/debugger/reference/idebugaddress-getaddress.md)
- [DEBUG_ADDRESS_UNION](../../../extensibility/debugger/reference/debug-address-union.md)
- [ADDRESS_KIND](../../../extensibility/debugger/reference/address-kind.md)
