---
description: Opisuje wynik powiązania punktu przerwania danych.
title: BP_RESOLUTION_DATA | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- BP_RESOLUTION_DATA
helpviewer_keywords:
- BP_RESOLUTION_DATA structure
ms.assetid: 9e0b9000-6a84-47b9-b07a-367a75764389
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 848a2b22ece8d3a51d7eef28b1f8baa7164ca22d
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/25/2021
ms.locfileid: "105054715"
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
Powiązane wyrażenie danych.

`bstrFunc`\
Nazwa funkcji, w której został powiązany punkt przerwania danych (jeśli istnieje).

`bstrImage`\
Nazwa modułu (na przykład MyModule.dll), z którym jest powiązany punkt przerwania danych.

`dwFlags`\
Wartość z wyliczenia [BP_RES_DATA_FLAGS](../../../extensibility/debugger/reference/bp-res-data-flags.md) , opisująca sposób implementacji punktu przerwania danych.

## <a name="remarks"></a>Uwagi
Ta struktura jest składową struktury [BP_RESOLUTION_LOCATION](../../../extensibility/debugger/reference/bp-resolution-location.md) , która jest z kolei członkiem struktury [BP_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-resolution-info.md) zwróconej przez metodę [GetResolutionInfo](../../../extensibility/debugger/reference/idebugbreakpointresolution2-getresolutioninfo.md) .

## <a name="requirements"></a>Wymagania
Nagłówek: Msdbg. h

Przestrzeń nazw: Microsoft. VisualStudio. Debugger. Interop

Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Zobacz też
- [Struktury i związki](../../../extensibility/debugger/reference/structures-and-unions.md)
- [BP_RESOLUTION_LOCATION](../../../extensibility/debugger/reference/bp-resolution-location.md)
- [BP_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-resolution-info.md)
- [GetResolutionInfo](../../../extensibility/debugger/reference/idebugbreakpointresolution2-getresolutioninfo.md)
