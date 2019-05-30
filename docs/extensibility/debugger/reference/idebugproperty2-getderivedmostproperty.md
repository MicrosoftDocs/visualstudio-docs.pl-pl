---
title: IDebugProperty2::GetDerivedMostProperty | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProperty2::GetDerivedMostProperty
helpviewer_keywords:
- IDebugProperty2::GetDerivedMostProperty
ms.assetid: cc86b461-62d1-4340-8209-c65037fd8b02
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 6b08ca2ad569935a117b8b1255bc740bf395c2ed
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/29/2019
ms.locfileid: "66343162"
---
# <a name="idebugproperty2getderivedmostproperty"></a>IDebugProperty2::GetDerivedMostProperty
Pobiera właściwość najbardziej pochodnej właściwości.

## <a name="syntax"></a>Składnia

```cpp
HRESULT GetDerivedMostProperty ( 
   IDebugProperty2** ppDerivedMost
);
```

```csharp
int GetDerivedMostProperty ( 
   out IDebugProperty2 ppDerivedMost
);
```

## <a name="parameters"></a>Parametry
`ppDerivedMost`\
[out] Zwraca [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) obiekt, który reprezentuje właściwość najbardziej pochodnej.

## <a name="return-value"></a>Wartość zwracana
 Jeśli operacja się powiedzie, zwraca `S_OK`; w przeciwnym razie zwraca kod błędu. Zwraca `S_GETDERIVEDMOST_NO_DERIVED_MOST` Jeśli nie ma właściwości najbardziej pochodnej do pobrania.

## <a name="remarks"></a>Uwagi
 Na przykład, jeśli ta właściwość opisuje obiekt, który implementuje `ClassRoot` , ale która jest faktycznie wystąpienia `ClassDerived` która pochodzi od `ClassRoot`, wówczas ta metoda zwraca [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) obiektu opisujące `ClassDerived` obiektu.

## <a name="see-also"></a>Zobacz także
- [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)