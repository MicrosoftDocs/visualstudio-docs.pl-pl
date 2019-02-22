---
title: IDebugProperty2::GetParent | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProperty2::GetParent
helpviewer_keywords:
- IDebugProperty2::GetParent
ms.assetid: 58780469-fe25-4d84-9187-67940ca0767f
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 30fa28ba52d40698447c6607be4b694466bb6127
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/22/2019
ms.locfileid: "56680155"
---
# <a name="idebugproperty2getparent"></a>IDebugProperty2::GetParent
Pobiera właściwość nadrzędna właściwości.

## <a name="syntax"></a>Składnia

```cpp
HRESULT GetParent ( 
   IDebugProperty2** ppParent
);
```

```csharp
int GetParent ( 
   out IDebugProperty2 ppParent
);
```

#### <a name="parameters"></a>Parametry
 `ppParent`

 [out] Zwraca [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) obiekt, który reprezentuje element nadrzędny właściwości.

## <a name="return-value"></a>Wartość zwracana
 Jeśli operacja się powiedzie, zwraca `S_OK`; w przeciwnym razie zwraca kod błędu. Zwraca `S_GETPARENT_NO_PARENT` Jeśli brak elementu nadrzędnego.

## <a name="see-also"></a>Zobacz też
- [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)