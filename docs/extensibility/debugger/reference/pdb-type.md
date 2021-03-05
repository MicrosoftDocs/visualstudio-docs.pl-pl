---
description: Ta struktura określa informacje o typie pola pobieranym z symbolu PDB.
title: PDB_TYPE | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- PDB_TYPE
helpviewer_keywords:
- PDB_TYPE structure
ms.assetid: 1c1bb772-77d6-4870-90b2-fd9247d0004e
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: ced96c1241c64abc764a052046e5ecab1a986bdc
ms.sourcegitcommit: f33ca1fc99f5d9372166431cefd0e0e639d20719
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/05/2021
ms.locfileid: "102222136"
---
# <a name="pdb_type"></a>PDB_TYPE

Ta struktura określa informacje o typie pola pobieranym z symbolu PDB.

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
Identyfikator aplikacji, z której pochodzi symbol. Służy do jednoznacznego identyfikowania wystąpienia aplikacji.

`guidModule`\
Identyfikator GUID modułu zawierającego to pole.

`symid`\
Identyfikator symbolu, który odnosi się do tego pola.

## <a name="remarks"></a>Uwagi

Ta struktura jest wyświetlana jako część Unii w strukturze [TYPE_INFO](../../../extensibility/debugger/reference/type-info.md) , gdy `dwKind` pole `TYPE_INFO` struktury jest ustawione na `TYPE_KIND_PDB` (wartość z wyliczenia [dwTYPE_KIND](../../../extensibility/debugger/reference/dwtype-kind.md) ).

## <a name="requirements"></a>Wymagania

Nagłówek: sh. h

Przestrzeń nazw: Microsoft. VisualStudio. Debugger. Interop

Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Zobacz też

- [Struktury i związki](../../../extensibility/debugger/reference/structures-and-unions.md)
- [TYPE_INFO](../../../extensibility/debugger/reference/type-info.md)
- [dwTYPE_KIND](../../../extensibility/debugger/reference/dwtype-kind.md)
