---
title: IDebugDefaultPort2::GetPortNotify | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugDefaultPort2::GetPortNotify
helpviewer_keywords:
- IDebugDefaultPort2::GetPortNotify
ms.assetid: 3ae715ee-9886-4694-a52b-59bb3b27467a
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 670dd128e6962c1e1d12f81eea03f9759fa56621
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80732404"
---
# <a name="idebugdefaultport2getportnotify"></a>IDebugDefaultPort2::GetPortNotify
Ta metoda pobiera interfejs [IDebugPortNotify2](../../../extensibility/debugger/reference/idebugportnotify2.md) dla tego portu.

## <a name="syntax"></a>Składnia

```cpp
HRESULT GetPortNotify(
   IDebugPortNotify2** ppPortNotify
);
```

```csharp
int GetPortNotify(
   out IDebugPortNotify2 ppPortNotify
);
```

## <a name="parameters"></a>Parametry
`ppPortNotify`\
[na zewnątrz] [Obiekt IDebugPortNotify2.](../../../extensibility/debugger/reference/idebugportnotify2.md)

## <a name="return-value"></a>Wartość zwracana
 Jeśli się `S_OK`powiedzie, zwraca ; w przeciwnym razie zwraca kod błędu.

## <a name="remarks"></a>Uwagi
 Zwykle `QueryInterface` metoda jest wywoływana na obiekcie implementującym interfejs [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md) w celu uzyskania interfejsu [IDebugPortNotify2.](../../../extensibility/debugger/reference/idebugportnotify2.md) Istnieją jednak okoliczności, w których żądany interfejs jest implementowany na inny obiekt. Ta metoda ukrywa te okoliczności `IDebugPortNotify2` i zwraca interfejs z najbardziej odpowiedniego obiektu.

## <a name="see-also"></a>Zobacz też
- [IDebugDefaultPort2](../../../extensibility/debugger/reference/idebugdefaultport2.md)
- [IDebugPortNotify2](../../../extensibility/debugger/reference/idebugportnotify2.md)
