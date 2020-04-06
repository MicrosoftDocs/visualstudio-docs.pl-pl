---
title: BP_RESOLUTION_DATA | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- BP_RESOLUTION_DATA
helpviewer_keywords:
- BP_RESOLUTION_DATA structure
ms.assetid: 9e0b9000-6a84-47b9-b07a-367a75764389
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 93a78f84c10af047e596459b68211b885d3c3085
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80737839"
---
# <a name="bp_resolution_data"></a>BP_RESOLUTION_DATA
Opisuje wynik powiązania punktu przerwania danych.

## <a name="syntax"></a>Składnia

```cpp
typedef struct _BP_RESOLUTION_DATA {
    BSTR              bstrDataExpr;
    BSTR              bstrFunc;
    BSTR              bstrImage;
    BP_RES_DATA_FLAGS dwFlags;
} BP_RESOLUTION_DATA;
```

```csharp
public struct BP_RESOLUTION_DATA {
    public string bstrDataExpr;
    public string bstrFunc;
    public string bstrImage;
    public uint   dwFlags;
};
```

## <a name="members"></a>Elementy członkowskie
`bstrDataExpr`\
Wyrażenie danych, które zostało powiązane.

`bstrFunc`\
Nazwa funkcji, do którego ma powiązany punkt przerwania danych (jeśli istnieje).

`bstrImage`\
Nazwa modułu (MyModule.dll, na przykład), że punkt przerwania danych ma powiązane w.

`dwFlags`\
Wartość z [BP_RES_DATA_FLAGS](../../../extensibility/debugger/reference/bp-res-data-flags.md) wyliczenia, opisujące sposób implementacji punktu przerwania danych.

## <a name="remarks"></a>Uwagi
Ta struktura jest członkiem [struktury BP_RESOLUTION_LOCATION,](../../../extensibility/debugger/reference/bp-resolution-location.md) która z kolei jest członkiem [struktury BP_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-resolution-info.md) zwracana przez [GetResolutionInfo](../../../extensibility/debugger/reference/idebugbreakpointresolution2-getresolutioninfo.md) metody.

## <a name="requirements"></a>Wymagania
Nagłówek: msdbg.h

Obszar nazw: Microsoft.VisualStudio.Debugger.Interop

Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Zobacz też
- [Struktury i związki](../../../extensibility/debugger/reference/structures-and-unions.md)
- [BP_RESOLUTION_LOCATION](../../../extensibility/debugger/reference/bp-resolution-location.md)
- [BP_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-resolution-info.md)
- [GetResolutionInfo](../../../extensibility/debugger/reference/idebugbreakpointresolution2-getresolutioninfo.md)
