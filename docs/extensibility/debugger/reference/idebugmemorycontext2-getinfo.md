---
title: IDebugMemoryContext2::GetInfo | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugMemoryContext2::GetInfo
helpviewer_keywords:
- GetInfo method
- IDebugMemoryContext2::GetInfo method
ms.assetid: 08c7f091-1816-4d64-8834-f9ecaac5c58d
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: a7ce91f8e7902db2665c0f87fd5dbff2188c3bc6
ms.sourcegitcommit: 19ec963ed6d585719cb83ba677434ea6580e0d1f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/24/2019
ms.locfileid: "66210512"
---
# <a name="idebugmemorycontext2getinfo"></a>IDebugMemoryContext2::GetInfo
Pobiera [CONTEXT_INFO](../../../extensibility/debugger/reference/context-info.md) strukturę, która opisuje kontekst.

## <a name="syntax"></a>Składnia

```cpp
HRESULT GetInfo( 
   CONTEXT_INFO_FIELDS dwFields,
   CONTEXT_INFO*       pInfo
);
```

```csharp
int GetInfo(
   enum_CONTEXT_INFO_FIELDS dwFields,
   CONTEXT_INFO[]           pinfo
);
```

## <a name="parameters"></a>Parametry
`dwFields`\
[in] Kombinacja flag z [CONTEXT_INFO_FIELDS](../../../extensibility/debugger/reference/context-info-fields.md) Wyliczenie wskazujące, które pola [CONTEXT_INFO](../../../extensibility/debugger/reference/context-info.md) struktury mają być wypełnić.

`pInfo`\
[out w] `CONTEXT_INFO` Strukturę, która jest wypełnione.

## <a name="return-value"></a>Wartość zwracana
 Jeśli operacja się powiedzie, zwraca `S_OK`; w przeciwnym razie zwraca kod błędu.

## <a name="see-also"></a>Zobacz także
- [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md)
- [CONTEXT_INFO_FIELDS](../../../extensibility/debugger/reference/context-info-fields.md)
- [CONTEXT_INFO](../../../extensibility/debugger/reference/context-info.md)