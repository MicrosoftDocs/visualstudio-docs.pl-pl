---
title: IDebugProperty2::GetDerivedMostProperty | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProperty2::GetDerivedMostProperty
helpviewer_keywords:
- IDebugProperty2::GetDerivedMostProperty
ms.assetid: cc86b461-62d1-4340-8209-c65037fd8b02
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 1227cb697dc78a8833e304d775fb4b1af85a2a69
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62916635"
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

#### <a name="parameters"></a>Parametry
 `ppDerivedMost`

 [out] Zwraca [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) obiekt, który reprezentuje właściwość najbardziej pochodnej.

## <a name="return-value"></a>Wartość zwracana
 Jeśli operacja się powiedzie, zwraca `S_OK`; w przeciwnym razie zwraca kod błędu. Zwraca `S_GETDERIVEDMOST_NO_DERIVED_MOST` Jeśli nie ma właściwości najbardziej pochodnej do pobrania.

## <a name="remarks"></a>Uwagi
 Na przykład, jeśli ta właściwość opisuje obiekt, który implementuje `ClassRoot` , ale która jest faktycznie wystąpienia `ClassDerived` która pochodzi od `ClassRoot`, wówczas ta metoda zwraca [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) obiektu opisujące `ClassDerived` obiektu.

## <a name="see-also"></a>Zobacz też
- [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)