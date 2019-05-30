---
title: IDebugModule3::LoadSymbols | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugModule3::LoadSymbols
helpviewer_keywords:
- IDebugModule3::LoadSymbols
ms.assetid: 7548c8c1-cbc6-48aa-a845-19058d4a85bb
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: e1b23e7b1ae837087db198795ffeda6a5827f045
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/29/2019
ms.locfileid: "66323844"
---
# <a name="idebugmodule3loadsymbols"></a>IDebugModule3::LoadSymbols
Ładuje symbole dla bieżącego modułu.

## <a name="syntax"></a>Składnia

```cpp
HRESULT LoadSymbols(
   void
);
```

```csharp
int LoadSymbols();
```

## <a name="return-value"></a>Wartość zwracana
 Jeśli metoda się powiedzie, zwraca `S_OK`. Jeśli nie powiedzie się, zwraca kod błędu.

## <a name="remarks"></a>Uwagi
 Ta metoda ładuje symbole z bieżącą ścieżkę wyszukiwania (może być zmienione przez wywołanie metody [SetSymbolPath](../../../extensibility/debugger/reference/idebugengine3-setsymbolpath.md) metody).

 Ta metoda jest preferowana nad [ReloadSymbols_Deprecated](../../../extensibility/debugger/reference/idebugmodule2-reloadsymbols-deprecated.md) metody.

## <a name="see-also"></a>Zobacz także
- [IDebugModule3](../../../extensibility/debugger/reference/idebugmodule3.md)
- [SetSymbolPath](../../../extensibility/debugger/reference/idebugengine3-setsymbolpath.md)