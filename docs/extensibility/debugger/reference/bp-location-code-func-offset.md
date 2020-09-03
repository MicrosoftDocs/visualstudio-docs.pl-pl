---
title: BP_LOCATION_CODE_FUNC_OFFSET | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- BP_LOCATION_CODE_FUNC_OFFSET
helpviewer_keywords:
- BP_LOCATION_CODE_FUNC_OFFSET structure
ms.assetid: ab38f7ca-fa01-4cf3-a06c-56cbb7207617
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
ms.openlocfilehash: 32331a5b628c27dc79d6a2e5919c8d268c96a3aa
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "80737995"
---
# <a name="bp_location_code_func_offset"></a>BP_LOCATION_CODE_FUNC_OFFSET
Opisuje lokalizację przesunięcia punktu przerwania w funkcji w kodzie.

## <a name="syntax"></a>Składnia

```cpp
typedef struct _BP_LOCATION_CODE_FUNC_OFFSET {
    BSTR                     bstrContext;
    IDebugFunctionPosition2* pFuncPos;
} BP_LOCATION_CODE_FUNC_OFFSET;
```

## <a name="members"></a>Elementy członkowskie
`bstrContext`\
Kontekst punktu przerwania, zazwyczaj nazwa metody lub funkcji, jak pokazano na stosie wywołań.

`pFuncPos`\
Obiekt [IDebugFunctionPosition2](../../../extensibility/debugger/reference/idebugfunctionposition2.md) , który opisuje nazwę funkcji i względną pozycję od początku funkcji.

## <a name="remarks"></a>Uwagi
Ta struktura jest składową struktury [BP_LOCATION](../../../extensibility/debugger/reference/bp-location.md) w ramach Unii.

`pFuncPos`Element członkowski wskazuje, gdzie ustawić punkt przerwania funkcji.

## <a name="requirements"></a>Wymagania
Nagłówek: Msdbg. h

Przestrzeń nazw: Microsoft. VisualStudio. Debugger. Interop

Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Zobacz też
- [Struktury i związki](../../../extensibility/debugger/reference/structures-and-unions.md)
- [BP_LOCATION](../../../extensibility/debugger/reference/bp-location.md)
- [IDebugFunctionPosition2](../../../extensibility/debugger/reference/idebugfunctionposition2.md)
