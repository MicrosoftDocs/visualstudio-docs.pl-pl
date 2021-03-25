---
description: Ta metoda zwraca typ obiektu, do którego wskazuje ten obiekt wskaźnika.
title: 'IDebugPointerField:: GetDereferencedField | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPointerField::GetDereferencedField
helpviewer_keywords:
- IDebugPointerField::GetDereferencedField method
ms.assetid: 8de988ab-cd79-4287-be72-3c900f2fe407
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: e54b378475cec191ca8395a7af5652ea6e93125f
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/25/2021
ms.locfileid: "105053675"
---
# <a name="idebugpointerfieldgetdereferencedfield"></a>IDebugPointerField::GetDereferencedField
Ta metoda zwraca typ obiektu, do którego wskazuje ten obiekt wskaźnika.

## <a name="syntax"></a>Składnia

```cpp
HRESULT GetDereferencedField(
   IDebugField** ppField
);
```

```csharp
int GetDereferencedField(
   out IDebugField ppField
);
```

## <a name="parameters"></a>Parametry
`ppField`\
określoną Zwraca [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) opisującą typ obiektu docelowego.

## <a name="return-value"></a>Wartość zwracana
 Jeśli powiedzie się, zwraca `S_OK` ; w przeciwnym razie zwraca kod błędu.

## <a name="remarks"></a>Uwagi
 Jeśli na przykład obiekt [IDebugPointerField](../../../extensibility/debugger/reference/idebugpointerfield.md) wskazuje liczbę całkowitą, typ [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) zwracany przez tę metodę opisuje ten typ liczba całkowita.

## <a name="see-also"></a>Zobacz też
- [IDebugPointerField](../../../extensibility/debugger/reference/idebugpointerfield.md)
- [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)
