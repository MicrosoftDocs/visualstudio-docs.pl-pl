---
title: BP_LOCATION_CODE_ADDRESS | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- BP_LOCATION_CODE_ADDRESS
helpviewer_keywords:
- BP_LOCATION_CODE_ADDRESS structure
ms.assetid: 83c9da8b-19d9-4be5-b225-854543654901
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
ms.openlocfilehash: c215630e522adabdbd285e00d4bcd87cae22a931
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80738042"
---
# <a name="bp_location_code_address"></a>BP_LOCATION_CODE_ADDRESS
Opisuje lokalizację punktu przerwania pod adresem w kodzie.

## <a name="syntax"></a>Składnia

```cpp
typedef struct _BP_LOCATION_CODE_ADDRESS {
    BSTR bstrContext;
    BSTR bstrModuleUrl;
    BSTR bstrFunction;
    BSTR bstrAddress;
} BP_LOCATION_CODE_ADDRESS;
```

## <a name="members"></a>Elementy członkowskie
`bstrContext`\
Kontekst punktu przerwania, zazwyczaj nazwa metody lub funkcji, jak widać na stosie wywołań.

`bstrModuleUrl`\
Adres URL modułu, który zawiera punkt przerwania.

`bstrFunction`\
Nazwa funkcji, która zawiera punkt przerwania.

`bstrAddress`\
Adres punktu przerwania, który jest analizowany przez oceniającego wyrażenie, aby powiązać go z [obiektem IDebugAddress.](../../../extensibility/debugger/reference/idebugaddress.md)

## <a name="remarks"></a>Uwagi
Struktura ta jest członkiem [struktury BP_LOCATION](../../../extensibility/debugger/reference/bp-location.md) jako część związku.

## <a name="requirements"></a>Wymagania
Nagłówek: msdbg.h

Obszar nazw: Microsoft.VisualStudio.Debugger.Interop

Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Zobacz też
- [Struktury i związki](../../../extensibility/debugger/reference/structures-and-unions.md)
- [BP_LOCATION](../../../extensibility/debugger/reference/bp-location.md)
- [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md)
