---
title: IDebugPropertyField::GetPropertyGetter | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPropertyField::GetPropertyGetter
helpviewer_keywords:
- IDebugPropertyField::GetPropertyGetter method
ms.assetid: ab9f861a-42ad-4a82-9ae6-2606176f755a
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: a50a9f28f7e430d37bb08139a6483218698b2eed
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/22/2019
ms.locfileid: "56706200"
---
# <a name="idebugpropertyfieldgetpropertygetter"></a>IDebugPropertyField::GetPropertyGetter
Pobiera metodę, która pobiera właściwość.

## <a name="syntax"></a>Składnia

```cpp
HRESULT GetPropertyGetter( 
   IDebugMethodField** ppField
);
```

```cpp
int GetPropertyGetter(
   out IDebugMethodField ppField
);
```

#### <a name="parameters"></a>Parametry
 `ppField`

 [out] Zwraca [IDebugMethodField](../../../extensibility/debugger/reference/idebugmethodfield.md) obiekt reprezentujący metodę, która pobiera właściwość.

## <a name="return-value"></a>Wartość zwracana
 Jeśli operacja się powiedzie, zwraca wartość S_OK; w przeciwnym razie zwraca kod błędu.

## <a name="remarks"></a>Uwagi
 Aby pobrać metodę, która ustawia właściwość [GetPropertySetter](../../../extensibility/debugger/reference/idebugpropertyfield-getpropertysetter.md) wywołania metody.

## <a name="see-also"></a>Zobacz też
- [IDebugPropertyField](../../../extensibility/debugger/reference/idebugpropertyfield.md)
- [GetPropertySetter](../../../extensibility/debugger/reference/idebugpropertyfield-getpropertysetter.md)
- [IDebugMethodField](../../../extensibility/debugger/reference/idebugmethodfield.md)