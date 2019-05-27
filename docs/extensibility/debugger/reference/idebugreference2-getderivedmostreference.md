---
title: IDebugReference2::GetDerivedMostReference | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugReference2::GetDerivedMostReference
helpviewer_keywords:
- IDebugReference2::GetDerivedMostReference
ms.assetid: 07253b74-7d39-48e0-8e85-ac8dfd919f6e
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 4b9534c144ae08a6fa5791518fea7d463819140b
ms.sourcegitcommit: 19ec963ed6d585719cb83ba677434ea6580e0d1f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/24/2019
ms.locfileid: "66212954"
---
# <a name="idebugreference2getderivedmostreference"></a>IDebugReference2::GetDerivedMostReference
Pobiera odniesienie najbardziej pochodnej odwołania. Zarezerwowane do użytku w przyszłości.

## <a name="syntax"></a>Składnia

```cpp
HRESULT GetDerivedMostReference( 
   IDebugReference2** ppDerivedMost
);
```

```csharp
int GetDerivedMostReference( 
   out IDebugReference2 ppDerivedMost
);
```

## <a name="parameters"></a>Parametry
`ppDerivedMost`\
[out] Zwraca [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md) obiekt, który reprezentuje właściwość najbardziej pochodnej.

## <a name="return-value"></a>Wartość zwracana
 Zawsze zwraca `E_NOTIMPL`.

## <a name="remarks"></a>Uwagi
 Na przykład, jeśli ta właściwość opisuje obiekt, który implementuje `ClassRoot` , ale która jest faktycznie wystąpienia `ClassDerived` która pochodzi od `ClassRoot`, wówczas ta metoda zwraca [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md) obiektu reprezentuje odwołanie do `ClassDerived` obiektu.

## <a name="see-also"></a>Zobacz także
- [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md)