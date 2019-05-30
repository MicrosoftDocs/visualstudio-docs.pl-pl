---
title: IDebugDefaultPort2::GetPortNotify | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugDefaultPort2::GetPortNotify
helpviewer_keywords:
- IDebugDefaultPort2::GetPortNotify
ms.assetid: 3ae715ee-9886-4694-a52b-59bb3b27467a
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: fd85f76ab0c882656ca79fe02296f30bdb83f523
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/29/2019
ms.locfileid: "66351763"
---
# <a name="idebugdefaultport2getportnotify"></a>IDebugDefaultPort2::GetPortNotify
Ta metoda pobiera [IDebugPortNotify2](../../../extensibility/debugger/reference/idebugportnotify2.md) interfejsu dla tego portu.

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
[out] [IDebugPortNotify2](../../../extensibility/debugger/reference/idebugportnotify2.md) obiektu.

## <a name="return-value"></a>Wartość zwracana
 Jeśli operacja się powiedzie, zwraca `S_OK`; w przeciwnym razie zwraca kod błędu.

## <a name="remarks"></a>Uwagi
 Zwykle `QueryInterface` metoda jest wywoływana w implementacji obiektu [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md) interfejs w celu uzyskania [IDebugPortNotify2](../../../extensibility/debugger/reference/idebugportnotify2.md) interfejsu. Istnieją jednak okoliczności, w których zaimplementowano żądanego interfejsu na inny obiekt. Ta metoda polega na schowaniu tych sytuacji i zwraca `IDebugPortNotify2` interfejs z najbardziej odpowiedniego obiektu.

## <a name="see-also"></a>Zobacz także
- [IDebugDefaultPort2](../../../extensibility/debugger/reference/idebugdefaultport2.md)
- [IDebugPortNotify2](../../../extensibility/debugger/reference/idebugportnotify2.md)