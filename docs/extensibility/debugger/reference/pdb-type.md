---
title: PDB_TYPE | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- PDB_TYPE
helpviewer_keywords:
- PDB_TYPE structure
ms.assetid: 1c1bb772-77d6-4870-90b2-fd9247d0004e
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 1f736d7d9b190fc46945e2f4f7c309b88c3e851f
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80714102"
---
# <a name="pdb_type"></a>PDB_TYPE

Ta struktura określa informacje o typie pola pobranym z symbolu PDB.

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
Identyfikator aplikacji, z której pochodzi symbol. Służy do jednoznacznej identyfikacji wystąpienia aplikacji.

`guidModule`\
Identyfikator GUID modułu zawierającego to pole.

`symid`\
Identyfikator symbolu odpowiadający temu polu.

## <a name="remarks"></a>Uwagi

Ta struktura pojawia się jako część unii w [strukturze TYPE_INFO,](../../../extensibility/debugger/reference/type-info.md) gdy `dwKind` pole `TYPE_INFO` struktury jest ustawiona na `TYPE_KIND_PDB` (wartość z [dwTYPE_KIND](../../../extensibility/debugger/reference/dwtype-kind.md) wyliczenia).

## <a name="requirements"></a>Wymagania

Nagłówek: sh.h

Obszar nazw: Microsoft.VisualStudio.Debugger.Interop

Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Zobacz też

- [Struktury i związki](../../../extensibility/debugger/reference/structures-and-unions.md)
- [TYPE_INFO](../../../extensibility/debugger/reference/type-info.md)
- [dwTYPE_KIND](../../../extensibility/debugger/reference/dwtype-kind.md)
