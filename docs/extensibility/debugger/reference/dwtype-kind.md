---
title: dwTYPE_KIND | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- dwTYPE_KIND
helpviewer_keywords:
- dwTYPE_KIND enumeration
ms.assetid: 6ff56b0f-c502-4e6c-9829-bfa05361b783
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: a9d790f12d3fc21bbae7373470746af2ebfe6dc9
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80737197"
---
# <a name="dwtype_kind"></a>dwTYPE_KIND
Określa sposób interpretowania typu obiektu [IDebugField.](../../../extensibility/debugger/reference/idebugfield.md)

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
Związek [TYPE_INFO](../../../extensibility/debugger/reference/type-info.md) należy interpretować jako strukturę [METADATA_TYPE.](../../../extensibility/debugger/reference/metadata-type.md)

`TYPE_KIND_PDB`\
Związek `TYPE_INFO` należy interpretować jako [strukturę PDB_TYPE.](../../../extensibility/debugger/reference/pdb-type.md)

`TYPE_KIND_BUILT`\
Związek `TYPE_INFO` należy interpretować jako [strukturę BUILT_TYPE.](../../../extensibility/debugger/reference/built-type.md)

## <a name="remarks"></a>Uwagi
Wartości tego wyliczenia są `dwKind` wyświetlane w polu [TYPE_INFO](../../../extensibility/debugger/reference/type-info.md) struktury i są używane do `type` określenia sposobu interpretowania elementu członkowskiego unii. Struktura `TYPE_INFO` jest zwracana przez wywołanie [metody GetTypeInfo.](../../../extensibility/debugger/reference/idebugfield-gettypeinfo.md)

## <a name="requirements"></a>Wymagania
Nagłówek: sh.h

Obszar nazw: Microsoft.VisualStudio.Debugger.Interop

Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Zobacz też
- [Wyliczenia](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [TYPE_INFO](../../../extensibility/debugger/reference/type-info.md)
- [GetTypeInfo](../../../extensibility/debugger/reference/idebugfield-gettypeinfo.md)
- [METADATA_TYPE](../../../extensibility/debugger/reference/metadata-type.md)
- [PDB_TYPE](../../../extensibility/debugger/reference/pdb-type.md)
- [BUILT_TYPE](../../../extensibility/debugger/reference/built-type.md)
