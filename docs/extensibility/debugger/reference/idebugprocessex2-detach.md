---
title: IDebugProcessEx2::Detach | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProcessEx2::Detach
helpviewer_keywords:
- IDebugProcessEx2::Detach method
ms.assetid: 66d54c2c-9302-47c8-9975-f30ed988ab29
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 2f016c078fcf19ec244fc4c0682d2caee81a2062
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/29/2019
ms.locfileid: "66311619"
---
# <a name="idebugprocessex2detach"></a>IDebugProcessEx2::Detach
Ta metoda informuje proces, czy sesja jest już debugowanie procesu.

## <a name="syntax"></a>Składnia

```cpp
HRESULT Detach( 
   IDebugSession2* pSession
);
```

```csharp
int Detach(
   IDebugSession2 pSession
);
```

## <a name="parameters"></a>Parametry
`pSession`\
[in] Wartość, która jednoznacznie identyfikuje sesję Aby odłączyć ten proces z.

## <a name="return-value"></a>Wartość zwracana
 Jeśli operacja się powiedzie, zwraca `S_OK`; w przeciwnym razie zwraca kod błędu.

## <a name="remarks"></a>Uwagi
 Interfejs przekazanej `pSession` jest należy traktować tylko jako plik cookie, wartość, która jednoznacznie identyfikuje Menedżer debugowania sesji, który pierwotnie dołączony do tego procesu; Brak metody w interfejsie podane są funkcjonalne.

## <a name="see-also"></a>Zobacz także
- [IDebugProcessEx2](../../../extensibility/debugger/reference/idebugprocessex2.md)