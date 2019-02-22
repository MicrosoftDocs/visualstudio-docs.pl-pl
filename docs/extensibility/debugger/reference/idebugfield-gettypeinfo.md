---
title: IDebugField::GetTypeInfo | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugField::GetTypeInfo
helpviewer_keywords:
- IDebugField::GetTypeInfo method
ms.assetid: bb5acfa3-04c3-4088-be84-9ff8926cd16f
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 7b881c3b5946428bf829ca4d971bb73f814b6d45
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/22/2019
ms.locfileid: "56700994"
---
# <a name="idebugfieldgettypeinfo"></a>IDebugField::GetTypeInfo
Ta metoda pobiera niezależnie od typu informacji na temat symboli lub typu.

## <a name="syntax"></a>Składnia

```cpp
HRESULT GetTypeInfo( 
   TYPE_INFO* pTypeInfo
);
```

```csharp
int GetTypeInfo(
   TYPE_INFO[] pTypeInfo
);
```

#### <a name="parameters"></a>Parametry
 `pTypeInfo`

 [out] Zwraca informację o typie w podanym [TYPE_INFO](../../../extensibility/debugger/reference/type-info.md) struktury.

## <a name="return-value"></a>Wartość zwracana
 Jeśli operacja się powiedzie, zwraca `S_OK`; w przeciwnym razie zwraca kod błędu.

## <a name="remarks"></a>Uwagi
 Niezależnie od typu informacji obejmuje, na przykład, element AppDomain, moduł i klasę, która zawiera symbol.

## <a name="see-also"></a>Zobacz też
- [GetType](../../../extensibility/debugger/reference/idebugfield-gettype.md)
- [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)
- [TYPE_INFO](../../../extensibility/debugger/reference/type-info.md)