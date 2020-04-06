---
title: UNMANAGED_ADDRESS_THIS_RELATIVE | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- UNMANAGED_ADDRESS_THIS_RELATIVE
helpviewer_keywords:
- UNMANAGED_ADDRESS_THIS_RELATIVE structure
ms.assetid: e6a91ace-2d47-4ff9-aefb-8d8b68eab0b2
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: ea493170c7b422129485fcea4248981a2b506001
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80713255"
---
# <a name="unmanaged_address_this_relative"></a>UNMANAGED_ADDRESS_THIS_RELATIVE
Ta struktura reprezentuje adres, który `this` jest`Me` względem wskaźnika (w języku Visual Basic).

## <a name="syntax"></a>Składnia

```cpp
typedef struct _tagUNMANAGED_THIS_RELATIVE {
   DWORD dwOffset;
   DWORD dwBitOffset;
   DWORD dwBitLength;
} UNMANAGED_ADDRESS_THIS_RELATIVE;
```

```csharp
public struct UNMANAGED_THIS_RELATIVE {
   public uint dwOffset;
   public uint dwBitOffset;
   public uint dwBitLength;
}
```

## <a name="members"></a>Elementy członkowskie
 `dwOffset`\
 Przesunięcie bajtów od pozycji bazowej (na przykład początek vtable klasy).

 `dwBitOffset`\
 Odsunięcie bitów z pozycji bazowej (zawsze 0, chyba że odnosi się do pola bitowego).

 `dwBitLength`\
 Liczba bitów reprezentujących adres (zawsze 0, chyba że odnosi się do pola bitowego).

## <a name="remarks"></a>Uwagi
 Ta struktura jest częścią unii w [strukturze DEBUG_ADDRESS_UNION,](../../../extensibility/debugger/reference/debug-address-union.md) `dwKind` gdy `DEBUG_ADDRESS_UNION` pole struktury `ADDRESS_KIND_UNMANAGED_THIS_RELATIVE` jest ustawiona na (wartość z [ADDRESS_KIND](../../../extensibility/debugger/reference/address-kind.md) wyliczenia).

## <a name="requirements"></a>Wymagania
 Nagłówek: sh.h

 Obszar nazw: Microsoft.VisualStudio.Debugger.Interop

 Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Zobacz też
- [Struktury i związki](../../../extensibility/debugger/reference/structures-and-unions.md)
- [DEBUG_ADDRESS_UNION](../../../extensibility/debugger/reference/debug-address-union.md)
