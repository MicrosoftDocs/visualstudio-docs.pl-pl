---
description: Porównuje obiekt z tym obiektem.
title: 'IDebugObject:: IsEqual | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugObject::IsEqual
helpviewer_keywords:
- IDebugObject::IsEqual method
ms.assetid: 4b76e663-ef2e-41ff-9be1-bf26d666a34a
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: cff388778ea584f589f92b5dc9dab11c060c953c
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/25/2021
ms.locfileid: "105054091"
---
# <a name="idebugobjectisequal"></a>IDebugObject::IsEqual
Porównuje obiekt z tym obiektem.

## <a name="syntax"></a>Składnia

```cpp
HRESULT IsEqual( 
   IDebugObject* pObject,
   BOOL*         pfIsEqual
);
```

```csharp
int IsEqual(
   IDebugObject pObject,
   out int      pfIsEqual
);
```

## <a name="parameters"></a>Parametry
`pObject`\
podczas Obiekt [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) reprezentujący obiekt, do którego ma zostać wykonane porównanie.

`pfIsEqual`\
określoną Zwraca wartość różną od zera ( `TRUE` ), jeśli wartości obiektów są równe; w przeciwnym razie zwraca zero ( `FALSE` ).

## <a name="return-value"></a>Wartość zwracana
 Jeśli powiedzie się, zwraca S_OK; w przeciwnym razie zwraca kod błędu.

## <a name="remarks"></a>Uwagi
 Zazwyczaj ta metoda umożliwia porównanie adresów wartości reprezentowanych przez `pObject` parametr i ten obiekt [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) ; Jeśli adresy są równe, obiekty można traktować jako równe.

## <a name="see-also"></a>Zobacz też
- [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)
