---
title: IDebugPropertyDestroyEvent2::GetDebugProperty | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPropertyDestroyEvent2::GetDebugProperty
helpviewer_keywords:
- IDebugPropertyDestroyEvent2::GetDebugProperty
ms.assetid: c96ae785-0ac8-4df4-8df3-15a8d7e13687
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 47f7c1646a01bef53f1b7a1cd2c99e147cfa1986
ms.sourcegitcommit: 19ec963ed6d585719cb83ba677434ea6580e0d1f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/24/2019
ms.locfileid: "66212356"
---
# <a name="idebugpropertydestroyevent2getdebugproperty"></a>IDebugPropertyDestroyEvent2::GetDebugProperty
Pobiera właściwości, które mają zostać zniszczone.

## <a name="syntax"></a>Składnia

```cpp
HRESULT GetDebugProperty ( 
   IDebugProperty2** ppProperty
);
```

```csharp
int GetDebugProperty ( 
   out IDebugProperty2 ppProperty
);
```

## <a name="parameters"></a>Parametry
`ppProperty`\
[out] Zwraca [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) obiekt, który reprezentuje właściwości, które mają zostać zniszczone.

## <a name="return-value"></a>Wartość zwracana
 Jeśli operacja się powiedzie, zwraca `S_OK`; w przeciwnym razie zwraca kod błędu.

## <a name="see-also"></a>Zobacz także
- [IDebugPropertyDestroyEvent2](../../../extensibility/debugger/reference/idebugpropertydestroyevent2.md)
- [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)