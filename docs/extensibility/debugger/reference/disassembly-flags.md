---
title: DISASSEMBLY_FLAGS | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- DISASSEMBLY_FLAGS
helpviewer_keywords:
- DISASSEMBLY_FLAGS enumeration
ms.assetid: c1ec5a4d-5d42-4660-932c-7348550140cb
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 0c4602fa1b8d30e9119bb39e925cf7768ae1cbcf
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/22/2019
ms.locfileid: "56682430"
---
# <a name="disassemblyflags"></a>DISASSEMBLY_FLAGS
Określa flagi dla dezasemblacji.

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

## <a name="members"></a>Elementy członkowskie
DF_DOCUMENTCHANGE wskazuje, że tej instrukcji jest w innym dokumencie niż poprzedni.

DF_DISABLED wskazuje, że ta instrukcja nie zostanie wykonany.

DF_INSTRUCTION_ACTIVE wskazuje, że ta instrukcja jest jednym z następnej instrukcji do wykonania (może istnieć więcej niż jeden).

DF_DATA wskazuje, że ta instrukcja jest naprawdę danych (nie kodzie).

DF_HASSOURCE wskazuje, że źródło zawiera tej instrukcji. Niektóre instrukcje, takich jak profilowania lub wyrzucania elementów kodu, ma nie odpowiadającego jej źródła.

DF_DOCUMENT_CHECKSUM wskazuje, że `bstrDocumentUrl` pole zawiera dane sumy kontrolnej po adres URL dokumentu. Zobacz sekcję Spostrzeżenia, aby [DisassemblyData](../../../extensibility/debugger/reference/disassemblydata.md) struktury przechowywania danych sumy kontrolnej.

## <a name="remarks"></a>Uwagi
Używane jako `dwFlags` członkiem [DisassemblyData](../../../extensibility/debugger/reference/disassemblydata.md) struktury.

Te flagi mogą być łączone przy użyciu bitowego operatora `OR`.

## <a name="requirements"></a>Wymagania
Header: msdbg.h

Przestrzeń nazw: Microsoft.VisualStudio.Debugger.Interop

Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Zobacz też
- [Wyliczenia](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [DisassemblyData](../../../extensibility/debugger/reference/disassemblydata.md)
