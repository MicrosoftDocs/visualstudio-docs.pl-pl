---
description: Służy do ustawiania punktów przerwania danych opartych na ciągu, który użytkownik może wprowadzić z zintegrowanego środowiska programistycznego (IDE).
title: BP_LOCATION_DATA_STRING | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- BP_LOCATION_DATA_STRING
helpviewer_keywords:
- BP_LOCATION_DATA_STRING structure
ms.assetid: 445d6f3f-95b0-47ac-85e2-51b778240687
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
ms.openlocfilehash: 98cfb12649fe85ce9e5f6b6a51a8c61243b5e9da
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/25/2021
ms.locfileid: "105096762"
---
# <a name="bp_location_data_string"></a>BP_LOCATION_DATA_STRING
Służy do ustawiania punktów przerwania danych opartych na ciągu, który użytkownik może wprowadzić z zintegrowanego środowiska programistycznego (IDE).

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
Obiekt [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md) , który reprezentuje wątek, w którym występuje punkt przerwania.

`bstrContext`\
Kontekst punktu przerwania w kodzie, zazwyczaj nazwa metody lub funkcji, jak pokazano na stosie wywołań.

`bstrDataExpr`\
Ciąg danych wprowadzony przez użytkownika w celu ustawienia punktu przerwania.

`dwNumElements`\
Liczba elementów w ciągu danych, w których występuje punkt przerwania.

## <a name="remarks"></a>Uwagi
Ta struktura jest składową struktury [BP_LOCATION](../../../extensibility/debugger/reference/bp-location.md) w ramach Unii.

## <a name="requirements"></a>Wymagania
Nagłówek: Msdbg. h

Przestrzeń nazw: Microsoft. VisualStudio. Debugger. Interop

Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Zobacz też
- [Struktury i związki](../../../extensibility/debugger/reference/structures-and-unions.md)
- [BP_LOCATION](../../../extensibility/debugger/reference/bp-location.md)
- [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)
