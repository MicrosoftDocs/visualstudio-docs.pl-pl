---
description: Pobiera odwołanie pochodne do odwołania.
title: 'IDebugReference2:: GetDerivedMostReference | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugReference2::GetDerivedMostReference
helpviewer_keywords:
- IDebugReference2::GetDerivedMostReference
ms.assetid: 07253b74-7d39-48e0-8e85-ac8dfd919f6e
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 9c482b05620f280b2948aefe7e95eb38682268c6
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/25/2021
ms.locfileid: "105071444"
---
# <a name="idebugreference2getderivedmostreference"></a>IDebugReference2::GetDerivedMostReference
Pobiera odwołanie pochodne do odwołania. Zarezerwowane do użytku w przyszłości.

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
określoną Zwraca obiekt [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md) , który reprezentuje właściwość pochodną.

## <a name="return-value"></a>Wartość zwracana
 Zawsze zwraca wartość `E_NOTIMPL`.

## <a name="remarks"></a>Uwagi
 Na przykład, jeśli ta właściwość opisuje obiekt, który implementuje `ClassRoot` , ale jest w rzeczywistości wystąpieniem, `ClassDerived` które pochodzi od `ClassRoot` , Metoda ta zwraca obiekt [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md) reprezentujący odwołanie do `ClassDerived` obiektu.

## <a name="see-also"></a>Zobacz też
- [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md)
