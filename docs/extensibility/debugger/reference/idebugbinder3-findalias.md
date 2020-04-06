---
title: IDebugBinder3::FindAlias | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugBinder3::FindAlias
helpviewer_keywords:
- IDebugBinder3::FindAlias method
ms.assetid: b8333701-2718-4983-8513-0875fb7cb730
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: f0a697e39d21b1c25a98c09ad6cc4837cca7a293
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80735862"
---
# <a name="idebugbinder3findalias"></a>IDebugBinder3::FindAlias
Ta metoda lokalizuje alias, o nazwie. Spowoduje to przeszukanie wszystkich aliasów w programie.

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
[w] Nazwa aliasu do znalezienia.

`ppAlias`\
[na zewnątrz] Znaleziono alias (jeśli istnieje) reprezentowany przez interfejs [IDebugAlias.](../../../extensibility/debugger/reference/idebugalias.md)

## <a name="return-value"></a>Wartość zwracana
 Jeśli się `S_OK`powiedzie, zwraca ; w przeciwnym `S_FALSE` razie zwraca (jeśli alias nie zostanie znaleziony) lub kod błędu.

## <a name="remarks"></a>Uwagi
 Ta metoda inicjuje obiekt docelowy do wartości null przed wywołaniem; następnie sprawdza wartość null, aby ustalić, czy alias został znaleziony.

## <a name="see-also"></a>Zobacz też
- [IDebugBinder3](../../../extensibility/debugger/reference/idebugbinder3.md)
- [IDebugAlias](../../../extensibility/debugger/reference/idebugalias.md)
