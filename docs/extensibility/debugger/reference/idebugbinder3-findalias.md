---
description: Ta metoda służy do lokalizowania aliasu pod nazwą.
title: 'IDebugBinder3:: FindAlias | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugBinder3::FindAlias
helpviewer_keywords:
- IDebugBinder3::FindAlias method
ms.assetid: b8333701-2718-4983-8513-0875fb7cb730
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: db4d5cad6d0c2990141e0dd3a824425b8b53145b
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/05/2021
ms.locfileid: "102167727"
---
# <a name="idebugbinder3findalias"></a>IDebugBinder3::FindAlias
Ta metoda służy do lokalizowania aliasu pod nazwą. Spowoduje to przeszukanie wszystkich aliasów w programie.

## <a name="syntax"></a>Składnia

```cpp
HRESULT FindAlias(
   LPCOLESTR     pcstrName,
   IDebugAlias** ppAlias
);
```

```csharp
int FindAlias(
   string          pcstrName,
   out IDebugAlias ppAlias
);
```

## <a name="parameters"></a>Parametry
`pcstrName`\
podczas Nazwa aliasu do znalezienia.

`ppAlias`\
określoną Znaleziono alias (jeśli istnieje) reprezentowany przez interfejs [IDebugAlias](../../../extensibility/debugger/reference/idebugalias.md) .

## <a name="return-value"></a>Wartość zwracana
 Jeśli powiedzie się, zwraca `S_OK` ; w przeciwnym razie zwraca `S_FALSE` (jeśli alias nie zostanie znaleziony) lub kod błędu.

## <a name="remarks"></a>Uwagi
 Ta metoda inicjuje obiekt docelowy do wartości null przed wywołaniem metody; następnie testuje wartość null w późniejszym zakresie, aby określić, czy alias został znaleziony.

## <a name="see-also"></a>Zobacz też
- [IDebugBinder3](../../../extensibility/debugger/reference/idebugbinder3.md)
- [IDebugAlias](../../../extensibility/debugger/reference/idebugalias.md)
