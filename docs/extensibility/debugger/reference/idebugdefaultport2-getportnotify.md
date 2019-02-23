---
title: IDebugDefaultPort2::GetPortNotify | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugDefaultPort2::GetPortNotify
helpviewer_keywords:
- IDebugDefaultPort2::GetPortNotify
ms.assetid: 3ae715ee-9886-4694-a52b-59bb3b27467a
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: e7e0cc45ba3f692f799deb568bcbb84cc5edf7bf
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/22/2019
ms.locfileid: "56712518"
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

#### <a name="parameters"></a>Parametry
 `ppPortNotify`

 [out] [IDebugPortNotify2](../../../extensibility/debugger/reference/idebugportnotify2.md) obiektu.

## <a name="return-value"></a>Wartość zwracana
 Jeśli operacja się powiedzie, zwraca `S_OK`; w przeciwnym razie zwraca kod błędu.

## <a name="remarks"></a>Uwagi
 Zwykle `QueryInterface` metoda jest wywoływana w implementacji obiektu [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md) interfejs w celu uzyskania [IDebugPortNotify2](../../../extensibility/debugger/reference/idebugportnotify2.md) interfejsu. Istnieją jednak okoliczności, w których zaimplementowano żądanego interfejsu na inny obiekt. Ta metoda polega na schowaniu tych sytuacji i zwraca `IDebugPortNotify2` interfejs z najbardziej odpowiedniego obiektu.

## <a name="see-also"></a>Zobacz też
- [IDebugDefaultPort2](../../../extensibility/debugger/reference/idebugdefaultport2.md)
- [IDebugPortNotify2](../../../extensibility/debugger/reference/idebugportnotify2.md)