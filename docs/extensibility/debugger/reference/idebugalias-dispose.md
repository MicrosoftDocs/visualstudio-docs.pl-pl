---
title: IDebugAlias::Dispose | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugAlias::Dispose
helpviewer_keywords:
- IDebugAlias::Dispose method
ms.assetid: e84909a4-d378-4f48-bf25-2c014c77c8e3
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: c84fc6887eb2594f9665924bd3eafa5452a3135c
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/29/2019
ms.locfileid: "66330278"
---
# <a name="idebugaliasdispose"></a>IDebugAlias::Dispose
Oznacza ten alias do usunięcia.

## <a name="syntax"></a>Składnia

```cpp
HRESULT Dispose();
```

```csharp
int Dispose();
```

## <a name="parameters"></a>Parametry
 Brak.

## <a name="return-value"></a>Wartość zwracana
 Jeśli operacja się powiedzie, zwraca wartość S_OK; w przeciwnym razie zwraca kod błędu.

## <a name="remarks"></a>Uwagi
 Gdy ta metoda jest wywoływana, alias nie jest już dostępna.

## <a name="see-also"></a>Zobacz także
- [IDebugAlias](../../../extensibility/debugger/reference/idebugalias.md)