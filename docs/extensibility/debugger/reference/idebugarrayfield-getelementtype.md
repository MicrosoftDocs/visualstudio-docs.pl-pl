---
title: IDebugArrayField::GetElementType | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugArrayField::GetElementType
helpviewer_keywords:
- IDebugArrayField::GetElementType method
ms.assetid: c46bf625-0a48-4cbb-8f1f-286356f2c065
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 13dabbf61999e8558fe08ecb65169dd43302d98f
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/29/2019
ms.locfileid: "66320954"
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

## <a name="parameters"></a>Parametry
`ppType`\
[out] Zwraca [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) obiekt, który opisuje typ elementu.

## <a name="return-value"></a>Wartość zwracana
 Jeśli operacja się powiedzie, zwraca wartość S_OK; w przeciwnym razie zwraca kod błędu.

## <a name="remarks"></a>Uwagi
 [IDebugArrayField](../../../extensibility/debugger/reference/idebugarrayfield.md) obiektu przyjęto założenie, że wszystkie elementy tablicy są tego samego typu.

## <a name="see-also"></a>Zobacz także
- [IDebugArrayField](../../../extensibility/debugger/reference/idebugarrayfield.md)
- [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)