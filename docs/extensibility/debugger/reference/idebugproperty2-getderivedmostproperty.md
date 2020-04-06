---
title: IDebugProperty2::GetDerivedMostProperty | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProperty2::GetDerivedMostProperty
helpviewer_keywords:
- IDebugProperty2::GetDerivedMostProperty
ms.assetid: cc86b461-62d1-4340-8209-c65037fd8b02
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 2086aded4361049d722ec36ba1d470ed8f7ac6e5
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80721504"
---
# <a name="idebugproperty2getderivedmostproperty"></a>IDebugProperty2::GetDerivedMostProperty
Pobiera właściwości pochodne większości właściwości właściwości.

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
[na zewnątrz] Zwraca obiekt [IDebugProperty2,](../../../extensibility/debugger/reference/idebugproperty2.md) który reprezentuje właściwość najbardziej pochodną.

## <a name="return-value"></a>Wartość zwracana
 Jeśli się `S_OK`powiedzie, zwraca ; w przeciwnym razie zwraca kod błędu. Zwraca, `S_GETDERIVEDMOST_NO_DERIVED_MOST` jeśli nie ma właściwości najbardziej pochodnych do pobrania.

## <a name="remarks"></a>Uwagi
 Na przykład jeśli ta właściwość opisuje `ClassRoot` obiekt, który implementuje, `ClassDerived` ale który `ClassRoot`jest faktycznie wystąpienia, który pochodzi od , a następnie `ClassDerived` zwraca [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) obiektu opisującego obiekt.

## <a name="see-also"></a>Zobacz też
- [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)
