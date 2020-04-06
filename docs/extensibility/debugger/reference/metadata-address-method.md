---
title: METADATA_ADDRESS_METHOD | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- METADATA_ADDRESS_METHOD
helpviewer_keywords:
- METADATA_ADDRESS_METHOD structure
ms.assetid: fc0e5370-1b4f-4867-837f-0d63c4b9dd09
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: bc3dd7a34e4f9a3e1b933781aeaf4e18cad7ec17
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80714455"
---
# <a name="metadata_address_method"></a>METADATA_ADDRESS_METHOD
Ta struktura reprezentuje adres metody klasy.

## <a name="syntax"></a>Składnia

```cpp
typedef struct _tagMETADATA_ADDRESS_METHOD {
   _mdToken tokMethod;
   DWORD    dwOffset;
   DWORD    dwVersion;
} METADATA_ADDRESS_METHOD;
```

```csharp
public struct METADATA_ADDRESS_METHOD {
   public int  tokMethod;
   public uint dwOffset;
   public uint dwVersion;
}
```

## <a name="members"></a>Elementy członkowskie
 `tokMethod`\
 Identyfikator metody.

 [C++] `_mdToken` jest `typedef` dla 32-bitowego `int`.

 `dwOffset`\
 Przesunięcie od początku klasy do tej metody (może reprezentować przesunięcie do vtable).

 `dwVersion`\
 Wersja metody (ta wartość jest unikatowa dla dostawcy symbolu).

## <a name="remarks"></a>Uwagi
 Ta struktura jest częścią unii w [strukturze DEBUG_ADDRESS_UNION,](../../../extensibility/debugger/reference/debug-address-union.md) `dwKind` gdy `DEBUG_ADDRESS_UNION` pole struktury `ADDRESS_KIND_METHOD` jest ustawiona na (wartość z [ADDRESS_KIND](../../../extensibility/debugger/reference/address-kind.md) wyliczenia).

## <a name="requirements"></a>Wymagania
 Nagłówek: sh.h

 Obszar nazw: Microsoft.VisualStudio.Debugger.Interop

 Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Zobacz też
- [Struktury i związki](../../../extensibility/debugger/reference/structures-and-unions.md)
- [DEBUG_ADDRESS_UNION](../../../extensibility/debugger/reference/debug-address-union.md)
- [ADDRESS_KIND](../../../extensibility/debugger/reference/address-kind.md)
