---
title: METADATA_ADDRESS_ARRAYELEM | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- METADATA_ADDRESS_ARRAYELEM
helpviewer_keywords:
- METADATA_ADDRESS_ARRAYELEM structure
ms.assetid: 24321be5-7c17-4038-82a1-c20a2b68ff3c
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 67e39eb8b03dd6f75ac39155bd744e03084beb0b
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80714553"
---
# <a name="metadata_address_arrayelem"></a>METADATA_ADDRESS_ARRAYELEM

Ta struktura reprezentuje element tablicy w tablicy.

## <a name="syntax"></a>Składnia

```cpp
typedef struct _tagMETADATA_ADDRESS_ARRAYELEM {
    _mdToken tokMethod;
    DWORD    dwIndex;
} METADATA_ADDRESS_ARRAYELEM;
```

```csharp
public struct METADATA_ADDRESS_ARRAYELEM {
    public int  tokMethod;
    public uint dwIndex;
}
```

## <a name="members"></a>Elementy członkowskie

`tokMethod`\
Identyfikator tablicy tego elementu jest częścią.

[C++] `_mdToken` jest `typedef` dla 32-bitowego `int`.

`dwIndex`\
Indeks tego elementu w tablicy.

## <a name="remarks"></a>Uwagi
Ta struktura jest częścią unii w [strukturze DEBUG_ADDRESS_UNION,](../../../extensibility/debugger/reference/debug-address-union.md) `dwKind` gdy `DEBUG_ADDRESS_UNION` pole struktury `ADDRESS_KIND_ARRAYELEM` jest ustawiona na (wartość z [ADDRESS_KIND](../../../extensibility/debugger/reference/address-kind.md) wyliczenia).

## <a name="requirements"></a>Wymagania
Nagłówek: sh.h

Obszar nazw: Microsoft.VisualStudio.Debugger.Interop

Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Zobacz też

- [Struktury i związki](../../../extensibility/debugger/reference/structures-and-unions.md)
- [DEBUG_ADDRESS_UNION](../../../extensibility/debugger/reference/debug-address-union.md)
- [ADDRESS_KIND](../../../extensibility/debugger/reference/address-kind.md)
