---
title: IDebugBinder::GetMemoryContext | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugBinder::GetMemoryContext
helpviewer_keywords:
- IDebugBinder::GetMemoryContext method
ms.assetid: 801c5b60-acff-4822-b23d-e9c7bbca8a0f
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 8d50126e26b836f7b53ee1abeb5c4988b74a2eed
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80735997"
---
# <a name="idebugbindergetmemorycontext"></a>IDebugBinder::GetMemoryContext
Ta metoda konwertuje lokalizację obiektu lub adres pamięci do kontekstu pamięci.

## <a name="syntax"></a>Składnia

```cpp
HRESULT GetMemoryContext( 
   IDebugField*           pField,
   DWORD                  dwConstant,
   IDebugMemoryContext2** ppMemCxt
);
```

```csharp
int GetMemoryContext(
   IDebugField              pField,
   uint                     dwConstant,
   out IDebugMemoryContext2 ppMemCxt
);
```

## <a name="parameters"></a>Parametry
`pField`\
[w] [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) opisujące obiekt do zlokalizowania. Jeśli `NULL`zamiast `dwConstant` tego użyj.

`dwConstant`\
[w] Stały adres pamięci, taki jak 0x5000.

`ppMemCxt`\
[na zewnątrz] Zwraca interfejs [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md) reprezentujący adres obiektu lub adres w pamięci.

## <a name="return-value"></a>Wartość zwracana
 Jeśli się `S_OK`powiedzie, zwraca ; w przeciwnym razie zwraca kod błędu.

## <a name="see-also"></a>Zobacz też
- [IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md)
- [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md)
- [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)
