---
title: BP_LOCATION_DATA_STRING | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- BP_LOCATION_DATA_STRING
helpviewer_keywords:
- BP_LOCATION_DATA_STRING structure
ms.assetid: 445d6f3f-95b0-47ac-85e2-51b778240687
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
ms.openlocfilehash: cf8e2958f55ca13ab050302a24ad9e5ae185d81a
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/29/2019
ms.locfileid: "66353095"
---
# <a name="bplocationdatastring"></a>BP_LOCATION_DATA_STRING
Używana do ustawiania punktów przerwania danych, które są oparte na ciąg, który użytkownik może wprowadzić ze zintegrowanego środowiska programistycznego (IDE).

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
[IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md) obiekt, który reprezentuje wątek, w którym występuje punkt przerwania.

`bstrContext`\
Kontekst punktu przerwania w kodzie, zazwyczaj nazwę metody lub funkcji wyświetlanego w stosie wywołań.

`bstrDataExpr`\
Ciąg danych, które użytkownik wprowadza ustawić punkt przerwania.

`dwNumElements`\
Liczba elementów w ciągu danych, w której występuje punkt przerwania.

## <a name="remarks"></a>Uwagi
Ta struktura jest elementem członkowskim [BP_LOCATION](../../../extensibility/debugger/reference/bp-location.md) struktur w ramach złożenia.

## <a name="requirements"></a>Wymagania
Header: msdbg.h

Przestrzeń nazw: Microsoft.VisualStudio.Debugger.Interop

Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Zobacz także
- [Struktury i związki](../../../extensibility/debugger/reference/structures-and-unions.md)
- [BP_LOCATION](../../../extensibility/debugger/reference/bp-location.md)
- [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)
