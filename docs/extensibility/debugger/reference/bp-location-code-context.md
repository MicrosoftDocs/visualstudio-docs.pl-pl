---
title: BP_LOCATION_CODE_CONTEXT | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- BP_LOCATION_CODE_CONTEXT
helpviewer_keywords:
- BP_LOCATION_CODE_CONTEXT structure
ms.assetid: 37412896-021a-4f73-9bb7-4125502c2e18
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
ms.openlocfilehash: a51665a22a01c17256c41d45d2970bea0f617140
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99948390"
---
# <a name="bp_location_code_context"></a>BP_LOCATION_CODE_CONTEXT
Opisuje lokalizację punktu przerwania, który jest powiązany bezpośrednio z adresem w debugowanym programie.

## <a name="syntax"></a>Składnia

```cpp
typedef struct _BP_LOCATION_CODE_CONTEXT {
    IDebugCodeContext2* pCodeContext;
} BP_LOCATION_CODE_CONTEXT;
```

## <a name="members"></a>Elementy członkowskie
`pCodeContext`\
Obiekt [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md) , który identyfikuje położenie punktu przerwania w kodzie.

## <a name="remarks"></a>Uwagi
Ta struktura jest składową struktury [BP_LOCATION](../../../extensibility/debugger/reference/bp-location.md) w ramach Unii.

## <a name="requirements"></a>Wymagania
Nagłówek: Msdbg. h

Przestrzeń nazw: Microsoft. VisualStudio. Debugger. Interop

Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Zobacz też
- [Struktury i związki](../../../extensibility/debugger/reference/structures-and-unions.md)
- [BP_LOCATION](../../../extensibility/debugger/reference/bp-location.md)
- [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md)
