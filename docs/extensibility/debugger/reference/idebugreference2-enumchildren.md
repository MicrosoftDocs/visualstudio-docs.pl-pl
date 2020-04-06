---
title: IDebugReference2::WyliczeniaDzieci | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugReference2::EnumChildren
helpviewer_keywords:
- IDebugReference2::EnumChildren
ms.assetid: 35b3c2f3-69f4-4013-b555-f847221f62e8
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 96b2fec782ce88dfb2200df35f56b35b304beda5
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80720632"
---
# <a name="idebugreference2enumchildren"></a>IDebugReference2::EnumChildren
Pobierz listę wybranych wiązek podrzędnych odniesienia. Zarezerwowane do użytku w przyszłości.

## <a name="syntax"></a>Składnia

```cpp
HRESULT EnumChildren ( 
   DEBUGREF_INFO_FLAGS        dwFields,
   DWORD                      dwRadix,
   DBG_ATTRIB_FLAGS           dwAttribFilter,
   LPCOLESTR                  pszNameFilter,
   DWORD                      dwTimeout,
   IEnumDebugReferenceInfo2** ppEnum
);
```

```csharp
int EnumChildren ( 
   enum_DEBUGREF_INFO_FLAGS     dwFields,
   uint                         dwRadix,
   enum_DBG_ATTRIB_FLAGS        dwAttribFilter,
   string                       pszNameFilter,
   uint                         dwTimeout,
   out IEnumDebugReferenceInfo2 ppEnum
);
```

## <a name="parameters"></a>Parametry
`dwFields`\
[w] Kombinacja flag z wyliczenia [DEBUGREF_INFO_FLAGS,](../../../extensibility/debugger/reference/debugref-info-flags.md) która określa, które pola w wyliczonych [DEBUG_REFERENCE_INFO](../../../extensibility/debugger/reference/debug-reference-info.md) struktur mają być wypełnione.

`dwRadix`\
[w] Radix do wykorzystania w formatowaniu wszelkich informacji liczbowych.

`dwAttribFilter`\
[w] Kombinacja flag z wyliczenia [DBG_ATTRIB_FLAGS,](../../../extensibility/debugger/reference/dbg-attrib-flags.md) który jest używany jako filtr `pszNameFilter` w połączeniu z parametrem, aby wybrać struktury, które mają być wyliczone.

`pszNameFilter`\
[w] Ciąg określający filtr, taki jak "MyX", używany `dwAttribFilter` w połączeniu z parametrem do wybierania struktur, które mają być wyliczone.

`dwTimeout`\
[w] Maksymalny czas ( w milisekundach) oczekiwania przed zwróceniem tej metody. Służy `INFINITE` do oczekiwania przez czas nieokreślony.

`ppEnum`\
[na zewnątrz] Zwraca obiekt [IEnumDebugReferenceInfo2](../../../extensibility/debugger/reference/ienumdebugreferenceinfo2.md) zawierający listę żądanych właściwości podrzędnych.

## <a name="return-value"></a>Wartość zwracana
 Zawsze zwraca wartość `E_NOTIMPL`.

## <a name="see-also"></a>Zobacz też
- [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md)
- [DEBUGREF_INFO_FLAGS](../../../extensibility/debugger/reference/debugref-info-flags.md)
- [DBG_ATTRIB_FLAGS](../../../extensibility/debugger/reference/dbg-attrib-flags.md)
- [IEnumDebugReferenceInfo2](../../../extensibility/debugger/reference/ienumdebugreferenceinfo2.md)
