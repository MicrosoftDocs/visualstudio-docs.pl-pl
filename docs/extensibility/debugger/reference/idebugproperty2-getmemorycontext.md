---
title: 'IDebugProperty2:: GetMemoryContext | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProperty2::GetMemoryContext
helpviewer_keywords:
- IDebugProperty2::GetMemoryContext
ms.assetid: 91793d25-790f-4881-a5c0-d0458e534514
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 8fa610af3ae00d30462c1a3a0c825e5a85722cdc
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "80721461"
---
# <a name="idebugproperty2getmemorycontext"></a>IDebugProperty2::GetMemoryContext
Pobiera kontekst pamięci wartości właściwości.

## <a name="syntax"></a>Składnia

```cpp
HRESULT GetMemoryContext ( 
   IDebugMemoryContext2** ppMemory
);
```

```csharp
int GetMemoryContext(
   out IDebugMemoryContext2 ppMemory
);
```

## <a name="parameters"></a>Parametry
`ppMemory`\
określoną Zwraca obiekt [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md) , który reprezentuje pamięć skojarzoną z tą właściwością.

## <a name="return-value"></a>Wartość zwracana
 Jeśli to się powiedzie, zwraca `S_OK` ; w przeciwnym razie zwraca kod błędu. Zwraca `S_GETMEMORYCONTEXT_NO_MEMORY_CONTEXT` Jeśli nie ma kontekstu pamięci do pobrania.

## <a name="see-also"></a>Zobacz też
- [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)
- [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md)
