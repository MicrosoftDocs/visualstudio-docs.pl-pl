---
description: Służy do ustawiania punktów przerwania kodu na podstawie ciągu, który użytkownik może wprowadzić z zintegrowanego środowiska programistycznego (IDE).
title: BP_LOCATION_CODE_STRING | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- BP_LOCATION_CODE_STRING
helpviewer_keywords:
- BP_LOCATION_CODE_STRING structure
ms.assetid: a4cd71c6-5052-45fe-907b-ebc6ca1df2e4
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
ms.openlocfilehash: 9c32a75e4976a81498033a656461d897e4f298a3
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/25/2021
ms.locfileid: "105096775"
---
# <a name="bp_location_code_string"></a>BP_LOCATION_CODE_STRING
Służy do ustawiania punktów przerwania kodu na podstawie ciągu, który użytkownik może wprowadzić z zintegrowanego środowiska programistycznego (IDE).

## <a name="syntax"></a>Składnia

```cpp
typedef struct _BP_LOCATION_CODE_STRING {
    BSTR bstrContext;
    BSTR bstrCodeExpr;
} BP_LOCATION_CODE_STRING;
```

## <a name="members"></a>Elementy członkowskie
`bstrContext`\
Kontekst punktu przerwania w kodzie, zazwyczaj nazwa metody lub funkcji, jak pokazano na stosie wywołań.

`bstrCodeExpr`\
Ciąg, w którym użytkownik wpisze, aby opisać punkt przerwania kodu.

## <a name="remarks"></a>Uwagi
Ta struktura jest składową struktury [BP_LOCATION](../../../extensibility/debugger/reference/bp-location.md) w ramach Unii.

## <a name="requirements"></a>Wymagania
Nagłówek: Msdbg. h

Przestrzeń nazw: Microsoft. VisualStudio. Debugger. Interop

Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Zobacz też
- [Struktury i związki](../../../extensibility/debugger/reference/structures-and-unions.md)
- [BP_LOCATION](../../../extensibility/debugger/reference/bp-location.md)
