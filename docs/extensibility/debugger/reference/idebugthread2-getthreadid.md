---
title: IDebugThread2::GetThreadId | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugThread2::GetThreadId
helpviewer_keywords:
- IDebugThread2::GetThreadId
ms.assetid: db8b1c07-6b86-47f9-b292-bac19c276d36
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: a7788cc09d92ff4c784fbcb7004393fe0d3074c8
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80718704"
---
# <a name="idebugthread2getthreadid"></a>IDebugThread2::GetThreadId
Pobiera identyfikator wątku systemowego.

## <a name="syntax"></a>Składnia

```cpp
HRESULT GetThreadId (
    DWORD* pdwThreadId
);
```

```csharp
int GetThreadId (
    out uint pdwThreadId
);
```

## <a name="parameters"></a>Parametry
`pdwThreadId`\
[na zewnątrz] Zwraca identyfikator wątku systemowego.

## <a name="return-value"></a>Wartość zwracana
Jeśli się `S_OK`powiedzie, zwraca ; w przeciwnym razie zwraca kod błędu.

## <a name="remarks"></a>Uwagi
Identyfikator wątku służy do identyfikowania wątku wśród wszystkich innych wątków w procesie.

## <a name="example"></a>Przykład
W poniższym przykładzie pokazano, jak `CProgram` zaimplementować tę metodę dla prostego obiektu, który implementuje interfejs [IDebugThread2.](../../../extensibility/debugger/reference/idebugthread2.md)

```cpp
HRESULT CProgram::GetThreadId(DWORD* pdwThreadId) {
    *pdwThreadId = GetCurrentThreadId();
    return NOERROR;
}
```

## <a name="see-also"></a>Zobacz też
- [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)
