---
title: IEnumDebugPrograms2::Reset | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumDebugPrograms2::Reset
helpviewer_keywords:
- IEnumDebugPrograms2::Reset
ms.assetid: b289242b-24ea-4df3-a811-20b0c8a903d6
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: f2f3f7b96b6176ac4df098993c7126a93a9dc618
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/29/2019
ms.locfileid: "66317026"
---
# <a name="ienumdebugprograms2reset"></a>IEnumDebugPrograms2::Reset
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
 Po ta metoda jest wywoływana, następnym wywołaniu [dalej](../../../extensibility/debugger/reference/ienumdebugprograms2-next.md) metoda zwraca pierwszy element wyliczenia.

## <a name="see-also"></a>Zobacz także
- [IEnumDebugPrograms2](../../../extensibility/debugger/reference/ienumdebugprograms2.md)