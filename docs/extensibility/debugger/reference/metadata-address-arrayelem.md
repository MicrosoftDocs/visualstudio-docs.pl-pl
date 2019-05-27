---
title: METADATA_ADDRESS_ARRAYELEM | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- METADATA_ADDRESS_ARRAYELEM
helpviewer_keywords:
- METADATA_ADDRESS_ARRAYELEM structure
ms.assetid: 24321be5-7c17-4038-82a1-c20a2b68ff3c
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: c2e78efb77bdd2bfaf2a7ef2b253110133b24934
ms.sourcegitcommit: 19ec963ed6d585719cb83ba677434ea6580e0d1f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/24/2019
ms.locfileid: "66212837"
---
# <a name="metadataaddressarrayelem"></a>METADATA_ADDRESS_ARRAYELEM

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
Identyfikator tablicy ten element jest częścią.

[C++] `_mdToken` jest `typedef` dla 32-bitowych `int`.

`dwIndex`\
Indeks tego elementu w tablicy.

## <a name="remarks"></a>Uwagi
Ta struktura jest częścią Unii w [DEBUG_ADDRESS_UNION](../../../extensibility/debugger/reference/debug-address-union.md) struktury, kiedy `dwKind` pole `DEBUG_ADDRESS_UNION` struktury jest ustawiona na `ADDRESS_KIND_ARRAYELEM` (wartość z zakresu od [ADDRESS_KIND](../../../extensibility/debugger/reference/address-kind.md) Wyliczenie).

## <a name="requirements"></a>Wymagania
Nagłówek: sh.h

Przestrzeń nazw: Microsoft.VisualStudio.Debugger.Interop

Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Zobacz także

- [Struktury i związki](../../../extensibility/debugger/reference/structures-and-unions.md)
- [DEBUG_ADDRESS_UNION](../../../extensibility/debugger/reference/debug-address-union.md)
- [ADDRESS_KIND](../../../extensibility/debugger/reference/address-kind.md)