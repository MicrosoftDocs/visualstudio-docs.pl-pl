---
description: Pobiera właściwość pochodną dla właściwości.
title: 'IDebugProperty2:: GetDerivedMostProperty | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProperty2::GetDerivedMostProperty
helpviewer_keywords:
- IDebugProperty2::GetDerivedMostProperty
ms.assetid: cc86b461-62d1-4340-8209-c65037fd8b02
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 6069091295371ea017547cdac6540e68ba2885e8
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/05/2021
ms.locfileid: "102171532"
---
# <a name="idebugproperty2getderivedmostproperty"></a>IDebugProperty2::GetDerivedMostProperty
Pobiera właściwość pochodną dla właściwości.

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
określoną Zwraca obiekt [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) , który reprezentuje właściwość pochodną.

## <a name="return-value"></a>Wartość zwracana
 Jeśli to się powiedzie, zwraca `S_OK` ; w przeciwnym razie zwraca kod błędu. Zwraca `S_GETDERIVEDMOST_NO_DERIVED_MOST` Jeśli nie istnieje właściwość pochodna, która ma zostać pobrana.

## <a name="remarks"></a>Uwagi
 Na przykład, jeśli ta właściwość opisuje obiekt, który implementuje `ClassRoot` , ale jest w rzeczywistości wystąpieniem, `ClassDerived` które pochodzi od `ClassRoot` , Metoda ta zwraca obiekt [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) opisujący `ClassDerived` obiekt.

## <a name="see-also"></a>Zobacz też
- [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)
