---
description: Określa kryteria do porównywania dwóch kontekstów dokumentów.
title: DOCCONTEXT_COMPARE | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- DOCCONTEXT_COMPARE
helpviewer_keywords:
- DOCCONTEXT_COMPARE enumeration
ms.assetid: ed947c34-b07e-4b69-8381-b6e7cb842862
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: f64e2e8ec365daa84cbd1d4f7e3e9bdc43391d5e
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/05/2021
ms.locfileid: "102170435"
---
# <a name="doccontext_compare"></a>DOCCONTEXT_COMPARE
Określa kryteria do porównywania dwóch kontekstów dokumentów.

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
Przeszedł jako argument do metody [Compare](../../../extensibility/debugger/reference/idebugdocumentcontext2-compare.md) .

Te wartości są używane do określania kryteriów porównania na potrzeby znajdowania pierwszego kontekstu dokumentu na liście. Kontekst dokumentu otrzymuje listę kontekstów dokumentu, aby porównać siebie z tą `IDebugDocumentContext2::Compare` metodą. Pierwszy kontekst dokumentu na liście, dla którego zwracany jest operator porównania `true` .

## <a name="requirements"></a>Wymagania
Nagłówek: Msdbg. h

Przestrzeń nazw: Microsoft. VisualStudio. Debugger. Interop

Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Zobacz też
- [Wyliczenia](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [Porównaj](../../../extensibility/debugger/reference/idebugdocumentcontext2-compare.md)
