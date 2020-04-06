---
title: METADATA_ADDRESS_RETVAL | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- METADATA_ADDRESS_RETVAL
helpviewer_keywords:
- METADATA_ADDRESS_RETVAL structure
ms.assetid: 5b0ec0fb-84b3-4ce7-8e24-becf3d881d7d
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: f2437d10078eb623e063b3292d96ef9bb4a9cf64
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80714274"
---
# <a name="metadata_address_retval"></a>METADATA_ADDRESS_RETVAL
Ta struktura reprezentuje wartość zwracaną z metody lub funkcji.

## <a name="syntax"></a>Składnia

```cpp
typedef struct _tagMETADATA_ADDRESS_RETVAL {
   _mdToken tokMethod;
   DWORD    dwCorType;
   DWORD    dwSigSize;
   BYTE     rgSig[10];
} METADATA_ADDRESS_RETVAL;
```

```csharp
public struct METADATA_ADDRESS_RETVAL {
   public int    tokMethod;
   public uint   dwCorType;
   public uint   dwSigSize;
   public byte[] rgSig;
}
```

## <a name="members"></a>Elementy członkowskie
 `tokMethod`\
 Identyfikator metody, dla.

 `dwCorType`\
 Podstawowy typ wartości zwracanej. Jest to wartość `CorElementType` z wyliczenia zdefiniowanego w pliku corhdr.h .NET Framework SDK.

 `dwSigSize`\
 Rozmiar podpisu wartości zwracanej (przechowywany w `rgSig`).

 `rgSig`\
 Tablica bajtów tworzących podpis wartości zwracanej.

## <a name="remarks"></a>Uwagi
 Ta struktura jest częścią unii w [strukturze DEBUG_ADDRESS_UNION,](../../../extensibility/debugger/reference/debug-address-union.md) `dwKind` gdy `DEBUG_ADDRESS_UNION` pole struktury `ADDRESS_KIND_RETVAL` jest ustawiona na (wartość z [ADDRESS_KIND](../../../extensibility/debugger/reference/address-kind.md) wyliczenia).

## <a name="requirements"></a>Wymagania
 Nagłówek: sh.h

 Obszar nazw: Microsoft.VisualStudio.Debugger.Interop

 Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Zobacz też
- [Struktury i związki](../../../extensibility/debugger/reference/structures-and-unions.md)
- [DEBUG_ADDRESS_UNION](../../../extensibility/debugger/reference/debug-address-union.md)
- [ADDRESS_KIND](../../../extensibility/debugger/reference/address-kind.md)
