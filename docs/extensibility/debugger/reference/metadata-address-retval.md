---
title: METADATA_ADDRESS_RETVAL | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- METADATA_ADDRESS_RETVAL
helpviewer_keywords:
- METADATA_ADDRESS_RETVAL structure
ms.assetid: 5b0ec0fb-84b3-4ce7-8e24-becf3d881d7d
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: b4453030f01e99dcb82c344f003e217e7b1c55b6
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/29/2019
ms.locfileid: "66333714"
---
# <a name="metadataaddressretval"></a>METADATA_ADDRESS_RETVAL
Ta struktura reprezentuje wartość zwracana z metody lub funkcji.

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
 Metody to wartość zwracana jest przeznaczony.

 `dwCorType`\
 Podstawowy typ wartości zwracanej. Jest to wartość z zakresu od `CorElementType` wyliczenie zdefiniowane w [!INCLUDE[dnprdnshort](../../../code-quality/includes/dnprdnshort_md.md)] pliku sekcję corhdr.h zestawu SDK.

 `dwSigSize`\
 Rozmiar podpisu zwracanej wartości (przechowywanej w `rgSig`).

 `rgSig`\
 Tablica bajtów tworzących podpis wartość zwracaną.

## <a name="remarks"></a>Uwagi
 Ta struktura jest częścią Unii w [DEBUG_ADDRESS_UNION](../../../extensibility/debugger/reference/debug-address-union.md) struktury, kiedy `dwKind` pole `DEBUG_ADDRESS_UNION` struktury jest ustawiona na `ADDRESS_KIND_RETVAL` (wartość z zakresu od [ADDRESS_KIND](../../../extensibility/debugger/reference/address-kind.md) Wyliczenie).

## <a name="requirements"></a>Wymagania
 Nagłówek: sh.h

 Przestrzeń nazw: Microsoft.VisualStudio.Debugger.Interop

 Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Zobacz także
- [Struktury i związki](../../../extensibility/debugger/reference/structures-and-unions.md)
- [DEBUG_ADDRESS_UNION](../../../extensibility/debugger/reference/debug-address-union.md)
- [ADDRESS_KIND](../../../extensibility/debugger/reference/address-kind.md)