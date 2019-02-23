---
title: IDebugEngine3::SetEngineGuid | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEngine3::SetEngineGuid
helpviewer_keywords:
- IDebugEngine3::SetEngineGuid
ms.assetid: 8bdfa05d-feb7-4d98-abac-77825a04c50f
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 14c1ad0e659df29c462d145e8c98166079857275
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/22/2019
ms.locfileid: "56702216"
---
# <a name="idebugengine3setengineguid"></a>IDebugEngine3::SetEngineGuid
Ta metoda ustawia aparat debugowania (DE) `GUID`.

## <a name="syntax"></a>Składnia

```cpp
HRESULT SetEngineGuid(
   GUID* guidEngine
);
```

```csharp
int SetEngineGuid(
   ref Guid guidEngine
);
```

#### <a name="parameters"></a>Parametry
 `guidEngine`

 [in] `GUID` silnika.

## <a name="return-value"></a>Wartość zwracana
 Jeśli operacja się powiedzie, zwraca `S_OK`; w przeciwnym razie zwraca kod błędu.

## <a name="see-also"></a>Zobacz też
- [IDebugEngine3](../../../extensibility/debugger/reference/idebugengine3.md)