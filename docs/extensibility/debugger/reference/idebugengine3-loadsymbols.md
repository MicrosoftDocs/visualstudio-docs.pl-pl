---
description: Ładuje (w razie potrzeby) symbole dla wszystkich modułów debugowanych przez ten aparat debugowania.
title: 'IDebugEngine3:: LoadSymbols | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEngine3::LoadSymbols
helpviewer_keywords:
- IDebugEngine3::LoadSymbols
ms.assetid: c846a440-1d91-4d48-b8f1-82e902ae152b
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: f4b4f210ef07ad10b35251582dd8a3c0fe3b0685
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/05/2021
ms.locfileid: "102153810"
---
# <a name="idebugengine3loadsymbols"></a>IDebugEngine3::LoadSymbols
Ładuje (w razie potrzeby) symbole dla wszystkich modułów debugowanych przez ten aparat debugowania.

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
 Jeśli powiedzie się, zwraca S_OK; w przeciwnym razie zwraca kod błędu.

## <a name="remarks"></a>Uwagi
 Spowoduje to załadowanie symboli debugowania dla wszystkich modułów, do których odwołuje się ten aparat debugowania. Symbole są ładowane tylko wtedy, gdy nie zostały jeszcze załadowane. Symbole są przeszukiwane w ścieżkach ustawionych przez wywołanie do [SetSymbolPath](../../../extensibility/debugger/reference/idebugengine3-setsymbolpath.md).

## <a name="see-also"></a>Zobacz też
- [SetSymbolPath](../../../extensibility/debugger/reference/idebugengine3-setsymbolpath.md)
- [IDebugEngine3](../../../extensibility/debugger/reference/idebugengine3.md)
