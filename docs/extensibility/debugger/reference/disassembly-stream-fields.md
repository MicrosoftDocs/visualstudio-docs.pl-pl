---
title: DISASSEMBLY_STREAM_FIELDS | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- DISASSEMBLY_STREAM_FIELDS
helpviewer_keywords:
- DISASSEMBLY_STREAM_FIELDS enumeration
ms.assetid: cfc9b4de-c756-4844-bea7-d9f186a51d1b
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: d10f2143cbefa86442e4087ac098020f5f2bd6ac
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80737355"
---
# <a name="disassembly_stream_fields"></a>DISASSEMBLY_STREAM_FIELDS
Określa, jakie informacje mają być pobierane o polu demontażu.

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
Inicjowanie/używanie tego `bstrAddress` pola.

`DSF_ADDRESSOFFSET`\
Inicjowanie/używanie tego `bstrAddressOffset` pola.

`DSF_CODEBYTES`\
Inicjowanie/używanie tego `bstrCodeBytes` pola.

`DSF_OPCODE`\
Inicjowanie/używanie tego `bstrOpCode` pola.

`DSF_OPERANDS`\
Inicjowanie/używanie tego `bstrOperands` pola.

`DSF_SYMBOL`\
Inicjowanie/używanie tego `bstrSymbol` pola.

`DSF_CODELOCATIONID`\
Inicjowanie/używanie tego `uCodeLocationId` pola.

`DSF_POSITION`\
Inicjuj/użyj pól `posBeg` i. `posEnd`

`DSF_DOCUMENTURL`\
Inicjowanie/używanie tego `bstrDocumentUrl` pola.

`DSF_BYTEOFFSET`\
Inicjowanie/używanie tego `dwByteOffset` pola.

`DSF_FLAGS`\
Zainicjować/użyć `dwFlags` pola ([DISASSEMBLY_FLAGS](../../../extensibility/debugger/reference/disassembly-flags.md)).

`DSF_OPERANDS_SYMBOLS`\
Uwzględnij nazwy `bstrOperands` symboli w polu.

`DSF_ALL`\
Określa wszystkie pola dla strumienia demontażu.

## <a name="remarks"></a>Uwagi
Przekazany jako parametr do [Read](../../../extensibility/debugger/reference/idebugdisassemblystream2-read.md) metody, aby wskazać, które pola [DisassemblyData](../../../extensibility/debugger/reference/disassemblydata.md) struktury mają być inicjowane.

Używane dla `dwFields` elementu `DisassemblyData` członkowskiego struktury, aby wskazać, które pola są używane i prawidłowe, gdy struktura jest zwracana.

Wartości te mogą być łączone z bitowym `OR`.

## <a name="requirements"></a>Wymagania
Nagłówek: msdbg.h

Obszar nazw: Microsoft.VisualStudio.Debugger.Interop

Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Zobacz też
- [Wyliczenia](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [DisassemblyData](../../../extensibility/debugger/reference/disassemblydata.md)
- [Odczyt](../../../extensibility/debugger/reference/idebugdisassemblystream2-read.md)
- [DISASSEMBLY_FLAGS](../../../extensibility/debugger/reference/disassembly-flags.md)
