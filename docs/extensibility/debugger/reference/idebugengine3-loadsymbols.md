---
title: IDebugEngine3::LoadSymbols | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEngine3::LoadSymbols
helpviewer_keywords:
- IDebugEngine3::LoadSymbols
ms.assetid: c846a440-1d91-4d48-b8f1-82e902ae152b
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 72c4fce5a7e8dd53093e21db2771d2176462e67c
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/29/2019
ms.locfileid: "66352523"
---
# <a name="idebugengine3loadsymbols"></a>IDebugEngine3::LoadSymbols
Symbole obciążenia (w razie potrzeby) dla wszystkich modułów, które jest debugowane tego aparatu debugowania.

## <a name="syntax"></a>Składnia

```cpp
HRESULT LoadSymbols();
```

```csharp
int LoadSymbols();
```

## <a name="parameters"></a>Parametry
 Brak.

## <a name="return-value"></a>Wartość zwracana
 Jeśli operacja się powiedzie, zwraca wartość S_OK; w przeciwnym razie zwraca kod błędu.

## <a name="remarks"></a>Uwagi
 Spowoduje to załadowanie symboli debugowania dla wszystkich modułów, które odwołuje się ten aparat debugowania. Symbole są ładowane tylko wtedy, gdy ich nie zostały jeszcze załadowane. Symbole są przeszukiwane w ścieżkach, ustaw przez wywołanie [SetSymbolPath](../../../extensibility/debugger/reference/idebugengine3-setsymbolpath.md).

## <a name="see-also"></a>Zobacz także
- [SetSymbolPath](../../../extensibility/debugger/reference/idebugengine3-setsymbolpath.md)
- [IDebugEngine3](../../../extensibility/debugger/reference/idebugengine3.md)