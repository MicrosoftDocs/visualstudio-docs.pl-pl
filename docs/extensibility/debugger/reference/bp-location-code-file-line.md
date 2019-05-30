---
title: BP_LOCATION_CODE_FILE_LINE | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- BP_LOCATION_CODE_FILE_LINE
helpviewer_keywords:
- BP_LOCATION_CODE_FILE_LINE structure
ms.assetid: 3ff32032-d412-44d3-91bf-870cc354a09e
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
ms.openlocfilehash: 9e2cdcce6895d88f4a3ea1096bd419d951a1f545
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/29/2019
ms.locfileid: "66319067"
---
# <a name="bplocationcodefileline"></a>BP_LOCATION_CODE_FILE_LINE
Zawiera dane dla lokalizacji punktu przerwania w określonym wierszu w pliku kodu źródłowego.

## <a name="syntax"></a>Składnia

```cpp
typedef struct _BP_LOCATION_CODE_FILE_LINE {
    BSTR                     bstrContext;
    IDebugDocumentPosition2* pDocPos;
} BP_LOCATION_CODE_FILE_LINE;
```

## <a name="members"></a>Elementy członkowskie
`bstrContext`\
Kontekst punktu przerwania, zazwyczaj nazwę metody lub funkcji wyświetlanego w stosie wywołań.

`pDocPos`\
[IDebugDocumentPosition2](../../../extensibility/debugger/reference/idebugdocumentposition2.md) obiekt, który reprezentuje dokumentu położenie punktu przerwania.

## <a name="remarks"></a>Uwagi
Ta struktura jest elementem członkowskim [BP_LOCATION](../../../extensibility/debugger/reference/bp-location.md) struktur w ramach złożenia.

## <a name="requirements"></a>Wymagania
Header: msdbg.h

Przestrzeń nazw: Microsoft.VisualStudio.Debugger.Interop

Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Zobacz także
- [Struktury i związki](../../../extensibility/debugger/reference/structures-and-unions.md)
- [BP_LOCATION](../../../extensibility/debugger/reference/bp-location.md)
- [IDebugDocumentPosition2](../../../extensibility/debugger/reference/idebugdocumentposition2.md)
