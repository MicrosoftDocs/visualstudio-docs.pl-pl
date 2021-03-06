---
description: Ta struktura reprezentuje adres metody klasy.
title: METADATA_ADDRESS_METHOD | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- METADATA_ADDRESS_METHOD
helpviewer_keywords:
- METADATA_ADDRESS_METHOD structure
ms.assetid: fc0e5370-1b4f-4867-837f-0d63c4b9dd09
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 4c79aa9e7592417ba3f42d86137908c350681eb8
ms.sourcegitcommit: f33ca1fc99f5d9372166431cefd0e0e639d20719
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/05/2021
ms.locfileid: "102222396"
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

 [C++] `_mdToken` jest `typedef` dla 32-bitowej `int` .

 `dwOffset`\
 Przesunięcie od klasy rozpoczyna się do tej metody (może reprezentować przesunięcie do tabeli metod wirtualnych).

 `dwVersion`\
 Wersja metody (ta wartość jest unikatowa dla dostawcy symboli).

## <a name="remarks"></a>Uwagi
 Ta struktura jest częścią Unii w strukturze [DEBUG_ADDRESS_UNION](../../../extensibility/debugger/reference/debug-address-union.md) , gdy `dwKind` pole `DEBUG_ADDRESS_UNION` struktury jest ustawione na `ADDRESS_KIND_METHOD` (wartość z wyliczenia [ADDRESS_KIND](../../../extensibility/debugger/reference/address-kind.md) ).

## <a name="requirements"></a>Wymagania
 Nagłówek: sh. h

 Przestrzeń nazw: Microsoft. VisualStudio. Debugger. Interop

 Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Zobacz też
- [Struktury i związki](../../../extensibility/debugger/reference/structures-and-unions.md)
- [DEBUG_ADDRESS_UNION](../../../extensibility/debugger/reference/debug-address-union.md)
- [ADDRESS_KIND](../../../extensibility/debugger/reference/address-kind.md)
