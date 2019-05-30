---
title: dwTYPE_KIND | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- dwTYPE_KIND
helpviewer_keywords:
- dwTYPE_KIND enumeration
ms.assetid: 6ff56b0f-c502-4e6c-9829-bfa05361b783
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 12fe23d53939303be6b7e6a20ff12d2524d71593
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/29/2019
ms.locfileid: "66318129"
---
# <a name="dwtypekind"></a>dwTYPE_KIND
Określa, jak interpretować typ [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) obiektu.

## <a name="syntax"></a>Składnia

```cpp
enum enum_dwTYPE_KIND {
    TYPE_KIND_METADATA = 0x0001,
    TYPE_KIND_PDB      = 0x0002,
    TYPE_KIND_BUILT    = 0x0003,
};

typedef DWORD dwTYPE_KIND;
```

```csharp
public enum enum_dwTYPE_KIND {
    TYPE_KIND_METADATA = 0x0001,
    TYPE_KIND_PDB      = 0x0002,
    TYPE_KIND_BUILT    = 0x0003,
};
```

## <a name="fields"></a>Pola
`TYPE_KIND_METADATA`\
[TYPE_INFO](../../../extensibility/debugger/reference/type-info.md) Unii powinno być interpretowane jako [METADATA_TYPE](../../../extensibility/debugger/reference/metadata-type.md) struktury.

`TYPE_KIND_PDB`\
`TYPE_INFO` Unii powinno być interpretowane jako [PDB_TYPE](../../../extensibility/debugger/reference/pdb-type.md) struktury.

`TYPE_KIND_BUILT`\
`TYPE_INFO` Unii powinno być interpretowane jako [BUILT_TYPE](../../../extensibility/debugger/reference/built-type.md) struktury.

## <a name="remarks"></a>Uwagi
Wartości to wyliczenie są wyświetlane w `dwKind` pole [TYPE_INFO](../../../extensibility/debugger/reference/type-info.md) struktury i służą do określenia sposobu interpretowania `type` Unii. `TYPE_INFO` Struktury jest zwracany przez wywołanie [GetTypeInfo](../../../extensibility/debugger/reference/idebugfield-gettypeinfo.md) metody.

## <a name="requirements"></a>Wymagania
Nagłówek: sh.h

Przestrzeń nazw: Microsoft.VisualStudio.Debugger.Interop

Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Zobacz także
- [Wyliczenia](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [TYPE_INFO](../../../extensibility/debugger/reference/type-info.md)
- [GetTypeInfo](../../../extensibility/debugger/reference/idebugfield-gettypeinfo.md)
- [METADATA_TYPE](../../../extensibility/debugger/reference/metadata-type.md)
- [PDB_TYPE](../../../extensibility/debugger/reference/pdb-type.md)
- [BUILT_TYPE](../../../extensibility/debugger/reference/built-type.md)
