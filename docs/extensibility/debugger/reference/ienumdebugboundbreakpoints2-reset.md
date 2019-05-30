---
title: IEnumDebugBoundBreakpoints2::Reset | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumDebugBoundBreakpoints2::Reset
helpviewer_keywords:
- IEnumDebugBoundBreakpoints2::Reset
ms.assetid: 0f0522a5-6a97-4c4e-859b-cc4476e6c527
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 1e02de3bced4f0e47b150d56003bba470d92c1b2
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/29/2019
ms.locfileid: "66351115"
---
# <a name="ienumdebugboundbreakpoints2reset"></a>IEnumDebugBoundBreakpoints2::Reset
Resetuje wyliczenia do pierwszego elementu.

## <a name="syntax"></a>Składnia

```cpp
HRESULT Reset(
   void
);
```

```csharp
int Reset();
```

## <a name="return-value"></a>Wartość zwracana
 Jeśli operacja się powiedzie, zwraca `S_OK`; w przeciwnym razie zwraca kod błędu.

## <a name="remarks"></a>Uwagi
 Po ta metoda jest wywoływana, następnym wywołaniu [dalej](../../../extensibility/debugger/reference/ienumdebugboundbreakpoints2-next.md) metoda zwraca pierwszy element wyliczenia.

## <a name="see-also"></a>Zobacz także
- [IEnumDebugBoundBreakpoints2](../../../extensibility/debugger/reference/ienumdebugboundbreakpoints2.md)