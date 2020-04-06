---
title: BP_LOCATION_DATA_STRING | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- BP_LOCATION_DATA_STRING
helpviewer_keywords:
- BP_LOCATION_DATA_STRING structure
ms.assetid: 445d6f3f-95b0-47ac-85e2-51b778240687
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
ms.openlocfilehash: 75f881feaaa2068abd98d771a63024f20435d98f
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80737965"
---
# <a name="bp_location_data_string"></a>BP_LOCATION_DATA_STRING
Służy do ustawiania punktów przerwania danych, które są oparte na ciągu, który użytkownik może wprowadzić ze zintegrowanego środowiska programistycznego (IDE).

## <a name="syntax"></a>Składnia

```cpp
typedef struct _BP_LOCATION_DATA_STRING {
    IDebugThread2* pThread;
    BSTR           bstrContext;
    BSTR           bstrDataExpr;
    DWORD          dwNumElements;
} BP_LOCATION_DATA_STRING;
```

## <a name="members"></a>Elementy członkowskie
`pThread`\
[IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md) obiekt, który reprezentuje wątek, na którym występuje punkt przerwania.

`bstrContext`\
Kontekst punktu przerwania w kodzie, zazwyczaj nazwa metody lub funkcji, jak widać na stosie wywołań.

`bstrDataExpr`\
Ciąg danych wprowadzony przez użytkownika w celu ustawienia punktu przerwania.

`dwNumElements`\
Liczba elementów w ciągu danych, w którym występuje punkt przerwania.

## <a name="remarks"></a>Uwagi
Struktura ta jest członkiem [struktury BP_LOCATION](../../../extensibility/debugger/reference/bp-location.md) jako część związku.

## <a name="requirements"></a>Wymagania
Nagłówek: msdbg.h

Obszar nazw: Microsoft.VisualStudio.Debugger.Interop

Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Zobacz też
- [Struktury i związki](../../../extensibility/debugger/reference/structures-and-unions.md)
- [BP_LOCATION](../../../extensibility/debugger/reference/bp-location.md)
- [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)
