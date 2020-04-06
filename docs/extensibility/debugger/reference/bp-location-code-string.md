---
title: BP_LOCATION_CODE_STRING | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- BP_LOCATION_CODE_STRING
helpviewer_keywords:
- BP_LOCATION_CODE_STRING structure
ms.assetid: a4cd71c6-5052-45fe-907b-ebc6ca1df2e4
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
ms.openlocfilehash: 0fc0d9a053faf69fde500333ab0faafa0e8d3448
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80737983"
---
# <a name="bp_location_code_string"></a>BP_LOCATION_CODE_STRING
Służy do ustawiania punktów przerwania kodu na podstawie ciągu, który użytkownik może wprowadzić ze zintegrowanego środowiska programistycznego (IDE).

## <a name="syntax"></a>Składnia

```cpp
typedef struct _BP_LOCATION_CODE_STRING {
    BSTR bstrContext;
    BSTR bstrCodeExpr;
} BP_LOCATION_CODE_STRING;
```

## <a name="members"></a>Elementy członkowskie
`bstrContext`\
Kontekst punktu przerwania w kodzie, zazwyczaj nazwa metody lub funkcji, jak widać na stosie wywołań.

`bstrCodeExpr`\
Ciąg, który użytkownik wpisuje w celu opisania punktu przerwania kodu.

## <a name="remarks"></a>Uwagi
Struktura ta jest członkiem [struktury BP_LOCATION](../../../extensibility/debugger/reference/bp-location.md) jako część związku.

## <a name="requirements"></a>Wymagania
Nagłówek: msdbg.h

Obszar nazw: Microsoft.VisualStudio.Debugger.Interop

Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Zobacz też
- [Struktury i związki](../../../extensibility/debugger/reference/structures-and-unions.md)
- [BP_LOCATION](../../../extensibility/debugger/reference/bp-location.md)
