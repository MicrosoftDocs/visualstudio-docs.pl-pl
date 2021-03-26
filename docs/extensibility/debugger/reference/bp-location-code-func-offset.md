---
description: Opisuje lokalizację przesunięcia punktu przerwania w funkcji w kodzie.
title: BP_LOCATION_CODE_FUNC_OFFSET | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- BP_LOCATION_CODE_FUNC_OFFSET
helpviewer_keywords:
- BP_LOCATION_CODE_FUNC_OFFSET structure
ms.assetid: ab38f7ca-fa01-4cf3-a06c-56cbb7207617
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
ms.openlocfilehash: 8e193171a82f21c92871cd226db09c3dc2713585
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/25/2021
ms.locfileid: "105096788"
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
