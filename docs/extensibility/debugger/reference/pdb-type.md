---
title: PDB_TYPE | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- PDB_TYPE
helpviewer_keywords:
- PDB_TYPE structure
ms.assetid: 1c1bb772-77d6-4870-90b2-fd9247d0004e
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 3121106b84111d20bf2915c0f9398fa92807cfd9
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/29/2019
ms.locfileid: "66349913"
---
# <a name="pdbtype"></a>PDB_TYPE

Ta struktura określa informacje o typie pola z symboli PDB.

## <a name="syntax"></a>Składnia

```cpp
typedef struct _tagTYPE_PDB {
    ULONG32 ulAppDomainID;
    GUID    guidModule;
    DWORD   symid;
} PDB_TYPE;
```

```csharp
public struct PDB_TYPE {
    public uint ulAppDomainID;
    public Guid guidModule;
    public uint symid;
};
```

## <a name="members"></a>Elementy członkowskie

`ulAppDomainID`\
Identyfikator aplikacji, z którego pochodzą symbolu. Służy do jednoznacznego identyfikowania wystąpienia aplikacji.

`guidModule`\
Identyfikator GUID moduł, który zawiera tego pola.

`symid`\
Identyfikator symbol, który odnosi się do tego pola.

## <a name="remarks"></a>Uwagi

Ta struktura jest wyświetlany jako część Unii w [TYPE_INFO](../../../extensibility/debugger/reference/type-info.md) struktury, kiedy `dwKind` pole `TYPE_INFO` struktury jest ustawiona na `TYPE_KIND_PDB` (wartość z zakresu od [dwTYPE_KIND](../../../extensibility/debugger/reference/dwtype-kind.md) Wyliczenie).

## <a name="requirements"></a>Wymagania

Nagłówek: sh.h

Przestrzeń nazw: Microsoft.VisualStudio.Debugger.Interop

Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Zobacz także

- [Struktury i związki](../../../extensibility/debugger/reference/structures-and-unions.md)
- [TYPE_INFO](../../../extensibility/debugger/reference/type-info.md)
- [dwTYPE_KIND](../../../extensibility/debugger/reference/dwtype-kind.md)
