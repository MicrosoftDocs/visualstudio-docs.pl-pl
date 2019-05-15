---
title: IDebugBinder3::FindAlias | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugBinder3::FindAlias
helpviewer_keywords:
- IDebugBinder3::FindAlias method
ms.assetid: b8333701-2718-4983-8513-0875fb7cb730
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 2b0185b0c3f7f26cfe9ffa8806c5049af323c517
ms.sourcegitcommit: 77b4ca625674658d5c5766e684fa0e2a07cad4da
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/14/2019
ms.locfileid: "65614956"
---
# <a name="idebugbinder3findalias"></a>IDebugBinder3::FindAlias
Ta metoda lokalizuje alias podanej nazwy. Przeszuka wszystkie aliasy w programie.

## <a name="syntax"></a>Składnia

```cpp
HRESULT FindAlias(
   LPCOLESTR     pcstrName,
   IDebugAlias** ppAlias
);
```

```csharp
int FindAlias(
   string          pcstrName,
   out IDebugAlias ppAlias
);
```

## <a name="parameters"></a>Parametry
`pcstrName`\
[in] Nazwa aliasu, aby znaleźć.

`ppAlias`\
[out] Alias znaleziono (jeśli istnieje) jest reprezentowane przez [IDebugAlias](../../../extensibility/debugger/reference/idebugalias.md) interfejsu.

## <a name="return-value"></a>Wartość zwracana
 Jeśli operacja się powiedzie, zwraca `S_OK`; w przeciwnym razie zwraca `S_FALSE` (Jeśli nie odnaleziono aliasu) lub kod błędu.

## <a name="remarks"></a>Uwagi
 Ta metoda inicjuje obiekt docelowy, na wartość null, przed wywołaniem; następnie sprawdza zawiera wartości null później określić, czy nie znaleziono aliasu.

## <a name="see-also"></a>Zobacz także
- [IDebugBinder3](../../../extensibility/debugger/reference/idebugbinder3.md)
- [IDebugAlias](../../../extensibility/debugger/reference/idebugalias.md)