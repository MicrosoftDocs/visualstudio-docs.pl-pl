---
title: DOCCONTEXT_COMPARE | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- DOCCONTEXT_COMPARE
helpviewer_keywords:
- DOCCONTEXT_COMPARE enumeration
ms.assetid: ed947c34-b07e-4b69-8381-b6e7cb842862
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 75e4453cae63f484961cb2d0f3385a703709f83b
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80737228"
---
# <a name="doccontext_compare"></a>DOCCONTEXT_COMPARE
Określa kryteria porównywania dwóch kontekstów dokumentu.

## <a name="syntax"></a>Składnia

```cpp
enum enum_DOCCONTEXT_COMPARE {
    DOCCONTEXT_EQUAL         = 0x0001,
    DOCCONTEXT_LESS_THAN     = 0x0002,
    DOCCONTEXT_GREATER_THAN  = 0x0003,
    DOCCONTEXT_SAME_DOCUMENT = 0x0004
};
typedef DWORD DOCCONTEXT_COMPARE;
```

```csharp
enum enum_DOCCONTEXT_COMPARE {
    DOCCONTEXT_EQUAL         = 0x0001,
    DOCCONTEXT_LESS_THAN     = 0x0002,
    DOCCONTEXT_GREATER_THAN  = 0x0003,
    DOCCONTEXT_SAME_DOCUMENT = 0x0004
};
```

## <a name="fields"></a>Pola
`DOCCONTEXT_EQUAL`\
Znajdź pierwszy kontekst dokumentu na liście, który jest równy kontekstowi dokumentu docelowego.

`DOCCONTEXT_LESS_THAN`\
Znajdź pierwszy kontekst dokumentu na liście, który jest mniejszy niż kontekst dokumentu docelowego.

`DOCCONTEXT_GREATER_THAN`\
Znajdź pierwszy kontekst dokumentu na liście, który jest większy niż kontekst dokumentu docelowego.

`DOCCONTEXT_SAME_DOCUMENT`\
Znajdź pierwszy kontekst dokumentu na liście, który znajduje się w tym samym dokumencie co kontekst dokumentu docelowego.

## <a name="remarks"></a>Uwagi
Przekazany jako argument do [Metody Porównania.](../../../extensibility/debugger/reference/idebugdocumentcontext2-compare.md)

Wartości te są używane do określania kryteriów porównania dla znalezienia pierwszego kontekstu dokumentu na liście. Kontekst dokumentu otrzymuje listę kontekstów dokumentu, aby porównać się z za pomocą `IDebugDocumentContext2::Compare` metody. Pierwszy kontekst dokumentu na liście, dla `true` którego jest zwracany operator porównania.

## <a name="requirements"></a>Wymagania
Nagłówek: msdbg.h

Obszar nazw: Microsoft.VisualStudio.Debugger.Interop

Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Zobacz też
- [Wyliczenia](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [Porównanie](../../../extensibility/debugger/reference/idebugdocumentcontext2-compare.md)
