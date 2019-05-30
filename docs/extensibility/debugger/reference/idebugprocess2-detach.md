---
title: IDebugProcess2::Detach | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProcess2::Detach
helpviewer_keywords:
- IDebugProcess2::Detach
ms.assetid: ee2b9084-2db1-4e49-a1d9-387284b7c3f8
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 3948ecce15b9b2b2e8b3bf974ecc2277d9fa0360
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/29/2019
ms.locfileid: "66353199"
---
# <a name="idebugprocess2detach"></a>IDebugProcess2::Detach
Odłącza debuger z tego procesu przez odłączenie wszystkich programów w procesie.

## <a name="syntax"></a>Składnia

```cpp
HRESULT Detach( 
   void 
);
```

```csharp
int Detach();
```

## <a name="return-value"></a>Wartość zwracana
 Jeśli operacja się powiedzie, zwraca `S_OK`; w przeciwnym razie zwraca kod błędu.

## <a name="remarks"></a>Uwagi
 Wszystkie programy i proces nadal działa, ale nie są już częścią sesji debugowania. Operacja odłączenia po pełne, nie ma więcej debugowania, który będą wysyłane zdarzenia dla tego procesu (i jego programów).

## <a name="see-also"></a>Zobacz także
- [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)