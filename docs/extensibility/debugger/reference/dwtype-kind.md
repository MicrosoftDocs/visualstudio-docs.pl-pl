---
title: dwTYPE_KIND | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- dwTYPE_KIND
helpviewer_keywords:
- dwTYPE_KIND enumeration
ms.assetid: 6ff56b0f-c502-4e6c-9829-bfa05361b783
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 2a33bdf1875426898a6db72831bee4d1d7ac1f9a
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62924494"
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

#### <a name="parameters"></a>Parametry
TYPE_KIND_METADATA [TYPE_INFO](../../../extensibility/debugger/reference/type-info.md) Unii powinno być interpretowane jako [METADATA_TYPE](../../../extensibility/debugger/reference/metadata-type.md) struktury.

TYPE_KIND_PDB `TYPE_INFO` Unii powinno być interpretowane jako [PDB_TYPE](../../../extensibility/debugger/reference/pdb-type.md) struktury.

TYPE_KIND_BUILT `TYPE_INFO` Unii powinno być interpretowane jako [BUILT_TYPE](../../../extensibility/debugger/reference/built-type.md) struktury.

## <a name="remarks"></a>Uwagi
Wartości to wyliczenie są wyświetlane w `dwKind` pole [TYPE_INFO](../../../extensibility/debugger/reference/type-info.md) struktury i służą do określenia sposobu interpretowania `type` Unii. `TYPE_INFO` Struktury jest zwracany przez wywołanie [GetTypeInfo](../../../extensibility/debugger/reference/idebugfield-gettypeinfo.md) metody.

## <a name="requirements"></a>Wymagania
Nagłówek: sh.h

Przestrzeń nazw: Microsoft.VisualStudio.Debugger.Interop

Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Zobacz też
- [Wyliczenia](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [TYPE_INFO](../../../extensibility/debugger/reference/type-info.md)
- [GetTypeInfo](../../../extensibility/debugger/reference/idebugfield-gettypeinfo.md)
- [METADATA_TYPE](../../../extensibility/debugger/reference/metadata-type.md)
- [PDB_TYPE](../../../extensibility/debugger/reference/pdb-type.md)
- [BUILT_TYPE](../../../extensibility/debugger/reference/built-type.md)
