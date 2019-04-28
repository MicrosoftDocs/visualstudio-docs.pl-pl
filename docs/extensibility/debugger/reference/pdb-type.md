---
title: PDB_TYPE | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- PDB_TYPE
helpviewer_keywords:
- PDB_TYPE structure
ms.assetid: 1c1bb772-77d6-4870-90b2-fd9247d0004e
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 5972a6da9422917ef61fb07c9124edca24032ee2
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62865432"
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

## <a name="parameters"></a>Parametry

`ulAppDomainID`

Identyfikator aplikacji, z którego pochodzą symbolu. Służy do jednoznacznego identyfikowania wystąpienia aplikacji.

`guidModule`

Identyfikator GUID moduł, który zawiera tego pola.

`symid`

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
