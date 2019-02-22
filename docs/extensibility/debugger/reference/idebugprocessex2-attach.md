---
title: IDebugProcessEx2::Attach | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProcessEx2::Attach
helpviewer_keywords:
- IDebugProcessEx2::Attach method
ms.assetid: f3334ed7-39bf-4d02-a338-36f567b9b287
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 0a39f674744d0b1e97e815d33c2d9564f4a39c0d
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/22/2019
ms.locfileid: "56698615"
---
# <a name="idebugprocessex2attach"></a>IDebugProcessEx2::Attach
Ta metoda informuje proces, że sesji jest teraz debugowanie procesu.

## <a name="syntax"></a>Składnia

```cpp
HRESULT Attach( 
   IDebugSession2* pSession
);
```

```csharp
int Attach(
   IDebugSession2 pSession
);
```

#### <a name="parameters"></a>Parametry
 `pSession`

 [in] Wartość, która jednoznacznie identyfikuje sesji dołączenie do tego procesu.

## <a name="return-value"></a>Wartość zwracana
 Jeśli operacja się powiedzie, zwraca `S_OK`; w przeciwnym razie zwraca kod błędu.

## <a name="remarks"></a>Uwagi
 Przekazanego interfejsu `pSession` jest traktowane tylko jako plik cookie, a wartość, która jednoznacznie identyfikuje Menedżer debugowania sesji, dołączenie do tego procesu; Brak metody w interfejsie podane są funkcjonalne.

## <a name="see-also"></a>Zobacz też
- [IDebugProcessEx2](../../../extensibility/debugger/reference/idebugprocessex2.md)