---
title: IDebugPortSupplier2::AddPort | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPortSupplier2::AddPort
helpviewer_keywords:
- IDebugPortSupplier2::AddPort
ms.assetid: df491161-6bf3-4fcc-b478-b9ec88ec995f
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 5c674b73ad6ec45b1e388f62fbd3103afb5daedb
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/22/2019
ms.locfileid: "56678232"
---
# <a name="idebugportsupplier2addport"></a>IDebugPortSupplier2::AddPort
Dodaje port.

## <a name="syntax"></a>Składnia

```cpp
HRESULT AddPort( 
   IDebugPortRequest2* pRequest,
   IDebugPort2**       ppPort
);
```

```csharp
int AddPort( 
   IDebugPortRequest2 pRequest,
   out IDebugPort2    ppPort
);
```

#### <a name="parameters"></a>Parametry
 `pRequest`

 [in] [IDebugPortRequest2](../../../extensibility/debugger/reference/idebugportrequest2.md) obiekt, który opisuje portu, który ma zostać dodana.

 `ppPort`

 [out] Zwraca [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md) obiekt, który reprezentuje numer portu.

## <a name="return-value"></a>Wartość zwracana
 Jeśli operacja się powiedzie, zwraca `S_OK`; w przeciwnym razie zwraca kod błędu.

## <a name="remarks"></a>Uwagi
 Ta metoda faktycznie tworzy żądany port, a także dodanie go do dostawcy portu wewnętrznej listy aktywnych portów. [CanAddPort](../../../extensibility/debugger/reference/idebugportsupplier2-canaddport.md) metodę można wywołać najpierw, aby uniknąć możliwych opóźnień czasochłonne.

## <a name="see-also"></a>Zobacz też
- [IDebugPortSupplier2](../../../extensibility/debugger/reference/idebugportsupplier2.md)
- [IDebugPortRequest2](../../../extensibility/debugger/reference/idebugportrequest2.md)
- [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md)
- [CanAddPort](../../../extensibility/debugger/reference/idebugportsupplier2-canaddport.md)