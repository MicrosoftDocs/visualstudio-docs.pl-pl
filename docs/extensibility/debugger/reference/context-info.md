---
title: CONTEXT_INFO | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CONTEXT_INFO
helpviewer_keywords:
- CONTEXT_INFO structure
ms.assetid: 6b513f4e-e7b0-4969-adf0-2205ccc1e09b
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 4838df34c14b936af15b8a7a582a6d30ea12bee1
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80737566"
---
# <a name="context_info"></a>CONTEXT_INFO
Ta struktura opisuje kontekst pamięci lub kontekst kodu.

## <a name="syntax"></a>Składnia

```cpp
typedef struct _tagCONTEXT_INFO {
    CONTEXT_INFO_FIELDS dwFields;
    BSTR                bstrModuleUrl;
    BSTR                bstrFunction;
    TEXT_POSITION       posFunctionOffset;
    BSTR                bstrAddress;
    BSTR                bstrAddressOffset;
    BSTR                bstrAddressAbsolute;
} CONTEXT_INFO;
```

```csharp
public struct CONTEXT_INFO {
    public uint          dwFields;
    public string        bstrModuleUrl;
    public string        bstrFunction;
    public TEXT_POSITION posFunctionOffset;
    public string        bstrAddress;
    public string        bstrAddressOffset;
    public string        bstrAddressAbsolute;
};
```

## <a name="members"></a>Elementy członkowskie
`dwFields`\
Kombinacja flag z [CONTEXT_INFO_FIELDS](../../../extensibility/debugger/reference/context-info-fields.md) wyliczenie, które określa, które pola są wypełniane<strong>.</strong>

`bstrModuleUrl`\
Nazwa modułu, w którym znajduje się kontekst.

`bstrFunction`\
Nazwa funkcji, w której znajduje się kontekst.

`posFunctionOffset`\
Struktura [TEXT_POSITION,](../../../extensibility/debugger/reference/text-position.md) która identyfikuje przesunięcie linii i kolumny funkcji skojarzonej z kontekstem kodu.

`bstrAddress`\
Adres w kodzie, w którym znajduje się dany kontekst.

`bstrAddressOffset`\
Przesunięcie adresu w kodzie, w którym znajduje się dany kontekst.

`bstrAddressAbsolute`\
Adres bezwzględny w pamięci, w którym znajduje się dany kontekst.

## <a name="remarks"></a>Uwagi
Ta struktura jest zwracana z wywołania [getInfo](../../../extensibility/debugger/reference/idebugmemorycontext2-getinfo.md) metody.

Typowym zastosowaniem dla tej struktury jest obsługa okna debugowania **pamięci.**

## <a name="requirements"></a>Wymagania
Nagłówek: msdbg.h

Obszar nazw: Microsoft.VisualStudio.Debugger.Interop

Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Zobacz też
- [Struktury i związki](../../../extensibility/debugger/reference/structures-and-unions.md)
- [GetInfo](../../../extensibility/debugger/reference/idebugmemorycontext2-getinfo.md)
- [CONTEXT_INFO_FIELDS](../../../extensibility/debugger/reference/context-info-fields.md)
- [TEXT_POSITION](../../../extensibility/debugger/reference/text-position.md)
