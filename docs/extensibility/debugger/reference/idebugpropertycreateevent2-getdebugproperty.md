---
title: IDebugPropertyCreateEvent2::GetDebugProperty | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPropertyCreateEvent2::GetDebugProperty
helpviewer_keywords:
- IDebugPropertyCreateEvent2::GetDebugProperty
ms.assetid: d7e43183-444c-4417-af19-82e28229f83a
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: a289707110aed49cbd5e9f8b68ce5579ec92223f
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62916494"
---
# <a name="idebugpropertycreateevent2getdebugproperty"></a>IDebugPropertyCreateEvent2::GetDebugProperty
Pobiera nową właściwość.

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

#### <a name="parameters"></a>Parametry
 `ppProperty`

 [out] Zwraca [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) obiekt, który reprezentuje nową właściwość.

## <a name="return-value"></a>Wartość zwracana
 Jeśli operacja się powiedzie, zwraca `S_OK`; w przeciwnym razie zwraca kod błędu.

## <a name="see-also"></a>Zobacz też
- [IDebugPropertyCreateEvent2](../../../extensibility/debugger/reference/idebugpropertycreateevent2.md)
- [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)