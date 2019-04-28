---
title: IDebugPortSupplier2::RemovePort | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPortSupplier2::RemovePort
helpviewer_keywords:
- IDebugPortSupplier2::RemovePort
ms.assetid: f5c1fbf2-9084-46f2-a682-7db963928df2
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: db48cc82e16f071ec55493e98570c6969324bfda
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62918031"
---
# <a name="idebugportsupplier2removeport"></a>IDebugPortSupplier2::RemovePort
Usuwa portu.

## <a name="syntax"></a>Składnia

```cpp
HRESULT RemovePort( 
   IDebugPort2* pPort
);
```

```csharp
int RemovePort( 
   IDebugPort2 pPort
);
```

#### <a name="parameters"></a>Parametry
 `pPort`

 [in] [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md) obiekt, który reprezentuje port do usunięcia.

## <a name="return-value"></a>Wartość zwracana
 Jeśli operacja się powiedzie, zwraca `S_OK`; w przeciwnym razie zwraca kod błędu.

## <a name="remarks"></a>Uwagi
 Ta metoda usuwa port z dostawcy portu wewnętrznej listy aktywnych portów.

## <a name="see-also"></a>Zobacz też
- [IDebugPortSupplier2](../../../extensibility/debugger/reference/idebugportsupplier2.md)
- [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md)