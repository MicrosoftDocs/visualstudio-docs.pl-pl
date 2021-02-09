---
title: 'IDebugPortSupplier2:: AddPort | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPortSupplier2::AddPort
helpviewer_keywords:
- IDebugPortSupplier2::AddPort
ms.assetid: df491161-6bf3-4fcc-b478-b9ec88ec995f
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 9e126612ed8b081e5ba0b703d14399ac74d78a9a
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99906314"
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

## <a name="parameters"></a>Parametry
`pRequest`\
podczas Obiekt [IDebugPortRequest2](../../../extensibility/debugger/reference/idebugportrequest2.md) , który opisuje port, który ma zostać dodany.

`ppPort`\
określoną Zwraca obiekt [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md) , który reprezentuje port.

## <a name="return-value"></a>Wartość zwracana
 Jeśli powiedzie się, zwraca `S_OK` ; w przeciwnym razie zwraca kod błędu.

## <a name="remarks"></a>Uwagi
 Ta metoda w rzeczywistości tworzy żądany port, a także dodaje go do wewnętrznej listy aktywnych portów dostawcy portów. Metodę [CanAddPort](../../../extensibility/debugger/reference/idebugportsupplier2-canaddport.md) można wywołać w pierwszej kolejności, aby uniknąć potencjalnych czasochłonnych opóźnień.

## <a name="see-also"></a>Zobacz też
- [IDebugPortSupplier2](../../../extensibility/debugger/reference/idebugportsupplier2.md)
- [IDebugPortRequest2](../../../extensibility/debugger/reference/idebugportrequest2.md)
- [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md)
- [CanAddPort](../../../extensibility/debugger/reference/idebugportsupplier2-canaddport.md)
