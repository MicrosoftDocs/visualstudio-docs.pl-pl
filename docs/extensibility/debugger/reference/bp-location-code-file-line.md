---
title: BP_LOCATION_CODE_FILE_LINE | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- BP_LOCATION_CODE_FILE_LINE
helpviewer_keywords:
- BP_LOCATION_CODE_FILE_LINE structure
ms.assetid: 3ff32032-d412-44d3-91bf-870cc354a09e
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 5ab7a0b226b7a8fac779e5c5109700a37e60d9d0
ms.sourcegitcommit: 752f03977f45169585e407ef719450dbe219b7fc
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/15/2019
ms.locfileid: "56315706"
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
`bstrContext`  
Kontekst punktu przerwania, zazwyczaj nazwę metody lub funkcji wyświetlanego w stosie wywołań.

`pDocPos`  
[IDebugDocumentPosition2](../../../extensibility/debugger/reference/idebugdocumentposition2.md) obiekt, który reprezentuje dokumentu położenie punktu przerwania.

## <a name="remarks"></a>Uwagi
Ta struktura jest elementem członkowskim [BP_LOCATION](../../../extensibility/debugger/reference/bp-location.md) struktur w ramach złożenia.

## <a name="requirements"></a>Wymagania
Header: msdbg.h

Przestrzeń nazw: Microsoft.VisualStudio.Debugger.Interop

Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Zobacz też
[Struktury i związki](../../../extensibility/debugger/reference/structures-and-unions.md)  
[BP_LOCATION](../../../extensibility/debugger/reference/bp-location.md)  
[IDebugDocumentPosition2](../../../extensibility/debugger/reference/idebugdocumentposition2.md)
