---
title: IDebugArrayField::GetElementType | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugArrayField::GetElementType
helpviewer_keywords:
- IDebugArrayField::GetElementType method
ms.assetid: c46bf625-0a48-4cbb-8f1f-286356f2c065
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: bd80c54d436698e14db69bb356bd0cca61aa6ea3
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62923985"
---
# <a name="idebugarrayfieldgetelementtype"></a>IDebugArrayField::GetElementType
Pobiera typ elementu w tablicy.

## <a name="syntax"></a>Składnia

```cpp
HRESULT GetElementType( 
   IDebugField** ppType
);
```

```csharp
int GetElementType(
   out IDebugField ppType
);
```

#### <a name="parameters"></a>Parametry
 `ppType`

 [out] Zwraca [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) obiekt, który opisuje typ elementu.

## <a name="return-value"></a>Wartość zwracana
 Jeśli operacja się powiedzie, zwraca wartość S_OK; w przeciwnym razie zwraca kod błędu.

## <a name="remarks"></a>Uwagi
 [IDebugArrayField](../../../extensibility/debugger/reference/idebugarrayfield.md) obiektu przyjęto założenie, że wszystkie elementy tablicy są tego samego typu.

## <a name="see-also"></a>Zobacz też
- [IDebugArrayField](../../../extensibility/debugger/reference/idebugarrayfield.md)
- [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)