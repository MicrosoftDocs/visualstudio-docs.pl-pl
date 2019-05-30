---
title: DISASSEMBLY_STREAM_FIELDS | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- DISASSEMBLY_STREAM_FIELDS
helpviewer_keywords:
- DISASSEMBLY_STREAM_FIELDS enumeration
ms.assetid: cfc9b4de-c756-4844-bea7-d9f186a51d1b
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 3499ce5bfe46f3185dd5c8ca9e2ada055544c8c8
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/29/2019
ms.locfileid: "66318261"
---
# <a name="disassemblystreamfields"></a>DISASSEMBLY_STREAM_FIELDS
Określa, jakie informacje należy pobrać o polu dezasemblacji.

## <a name="syntax"></a>Składnia

```cpp
enum enum_DISASSEMBLY_STREAM_FIELDS {
    DSF_ADDRESS          = 0x00000001,
    DSF_ADDRESSOFFSET    = 0x00000002,
    DSF_CODEBYTES        = 0x00000004,
    DSF_OPCODE           = 0x00000008,
    DSF_OPERANDS         = 0x00000010,
    DSF_SYMBOL           = 0x00000020,
    DSF_CODELOCATIONID   = 0x00000040,
    DSF_POSITION         = 0x00000080,
    DSF_DOCUMENTURL      = 0x00000100,
    DSF_BYTEOFFSET       = 0x00000200,
    DSF_FLAGS            = 0x00000400,
    DSF_OPERANDS_SYMBOLS = 0x00010000,
    DSF_ALL              = 0x000107ff
};
typedef DWORD DISASSEMBLY_STREAM_FIELDS;
```

```csharp
public enum enum_DISASSEMBLY_STREAM_FIELDS {
    DSF_ADDRESS          = 0x00000001,
    DSF_ADDRESSOFFSET    = 0x00000002,
    DSF_CODEBYTES        = 0x00000004,
    DSF_OPCODE           = 0x00000008,
    DSF_OPERANDS         = 0x00000010,
    DSF_SYMBOL           = 0x00000020,
    DSF_CODELOCATIONID   = 0x00000040,
    DSF_POSITION         = 0x00000080,
    DSF_DOCUMENTURL      = 0x00000100,
    DSF_BYTEOFFSET       = 0x00000200,
    DSF_FLAGS            = 0x00000400,
    DSF_OPERANDS_SYMBOLS = 0x00010000,
    DSF_ALL              = 0x000107ff
};
```

## <a name="fields"></a>Pola
`DSF_ADDRESS`\
Inicjowanie bądź użyj `bstrAddress` pola.

`DSF_ADDRESSOFFSET`\
Inicjowanie bądź użyj `bstrAddressOffset` pola.

`DSF_CODEBYTES`\
Inicjowanie bądź użyj `bstrCodeBytes` pola.

`DSF_OPCODE`\
Inicjowanie bądź użyj `bstrOpCode` pola.

`DSF_OPERANDS`\
Inicjowanie bądź użyj `bstrOperands` pola.

`DSF_SYMBOL`\
Inicjowanie bądź użyj `bstrSymbol` pola.

`DSF_CODELOCATIONID`\
Inicjowanie bądź użyj `uCodeLocationId` pola.

`DSF_POSITION`\
Inicjowanie bądź użyj `posBeg` i `posEnd` pola.

`DSF_DOCUMENTURL`\
Inicjowanie bądź użyj `bstrDocumentUrl` pola.

`DSF_BYTEOFFSET`\
Inicjowanie bądź użyj `dwByteOffset` pola.

`DSF_FLAGS`\
Inicjowanie bądź użyj `dwFlags` ([DISASSEMBLY_FLAGS](../../../extensibility/debugger/reference/disassembly-flags.md)) pola.

`DSF_OPERANDS_SYMBOLS`\
Dołącz nazwy symbolu w `bstrOperands` pola.

`DSF_ALL`\
Określa wszystkie pola dla strumienia dezasemblacji.

## <a name="remarks"></a>Uwagi
Przekazany jako parametr do [odczytu](../../../extensibility/debugger/reference/idebugdisassemblystream2-read.md) metodę, aby wskazać, które pola [DisassemblyData](../../../extensibility/debugger/reference/disassemblydata.md) struktury, które mają zostać zainicjowane.

Używany do `dwFields` członkiem `DisassemblyData` struktury, aby wskazać, pola, które są używane i ważne, gdy zwracany jest struktura.

Te wartości mogą być łączone przy użyciu bitowego operatora `OR`.

## <a name="requirements"></a>Wymagania
Header: msdbg.h

Przestrzeń nazw: Microsoft.VisualStudio.Debugger.Interop

Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Zobacz także
- [Wyliczenia](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [DisassemblyData](../../../extensibility/debugger/reference/disassemblydata.md)
- [Read](../../../extensibility/debugger/reference/idebugdisassemblystream2-read.md)
- [DISASSEMBLY_FLAGS](../../../extensibility/debugger/reference/disassembly-flags.md)
