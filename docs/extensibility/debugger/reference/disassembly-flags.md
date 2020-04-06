---
title: DISASSEMBLY_FLAGS | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- DISASSEMBLY_FLAGS
helpviewer_keywords:
- DISASSEMBLY_FLAGS enumeration
ms.assetid: c1ec5a4d-5d42-4660-932c-7348550140cb
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: ba6d9db3ad2cb1f9bbc9e3cea27aba939c6dd499
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80737373"
---
# <a name="disassembly_flags"></a>DISASSEMBLY_FLAGS
Określa flagi do demontażu.

## <a name="syntax"></a>Składnia

```cpp
enum enum_DISASSEMBLY_FLAGS {
    DF_DOCUMENTCHANGE     = 0x00000001,
    DF_DISABLED           = 0x00000002,
    DF_INSTRUCTION_ACTIVE = 0x00000004,
    DF_DATA               = 0x00000008,
    DF_HASSOURCE          = 0x00000010,
    DF_DOCUMENT_CHECKSUM  = 0x00000020
};
typedef DWORD DISASSEMBLY_FLAGS;
```

```csharp
public enum enum_DISASSEMBLY_FLAGS {
    DF_DOCUMENTCHANGE     = 0x00000001,
    DF_DISABLED           = 0x00000002,
    DF_INSTRUCTION_ACTIVE = 0x00000004,
    DF_DATA               = 0x00000008,
    DF_HASSOURCE          = 0x00000010,
    DF_DOCUMENT_CHECKSUM  = 0x00000020
};
```

## <a name="fields"></a>Pola
`DF_DOCUMENTCHANGE`\
Wskazuje, że ta instrukcja znajduje się w innym dokumencie niż poprzedni.

`DF_DISABLED`\
Wskazuje, że ta instrukcja nie zostanie wykonana.

`DF_INSTRUCTION_ACTIVE`\
Wskazuje, że ta instrukcja jest jedną z następnych instrukcji do wykonania (może być więcej niż jedna).

`DF_DATA`\
Wskazuje, że ta instrukcja jest naprawdę dane (nie kod).

`DF_HASSOURCE`\
Wskazuje, że ta instrukcja ma źródło. Niektóre instrukcje, takie jak profilowanie lub kod wyrzucania elementów bezużytecznych, nie mają odpowiedniego źródła.

`DF_DOCUMENT_CHECKSUM`\
Wskazuje, `bstrDocumentUrl` że pole zawiera dane sumy kontrolnej po adresie URL dokumentu. Zobacz uwagi sekcji dla [DisassemblyData](../../../extensibility/debugger/reference/disassemblydata.md) struktury jak dane sumy kontrolnej są przechowywane.

## <a name="remarks"></a>Uwagi
Używany jako `dwFlags` element członkowski [struktury DisassemblyData.](../../../extensibility/debugger/reference/disassemblydata.md)

Flagi te mogą być łączone z bitowym `OR`.

## <a name="requirements"></a>Wymagania
Nagłówek: msdbg.h

Obszar nazw: Microsoft.VisualStudio.Debugger.Interop

Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Zobacz też
- [Wyliczenia](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [DisassemblyData](../../../extensibility/debugger/reference/disassemblydata.md)
