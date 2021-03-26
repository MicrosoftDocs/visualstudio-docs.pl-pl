---
description: Pobiera klasę, która należy do tej klasy.
title: 'IDebugClassField:: GetEnclosingClass | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugClassField::GetEnclosingClass
helpviewer_keywords:
- IDebugClassField::GetEnclosingClass method
ms.assetid: a0c12e3c-9ea0-4dfb-9e45-8cea18725022
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: c59eb2559634c67b210f4fc3b4ce41743346c8ea
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/25/2021
ms.locfileid: "105088487"
---
# <a name="idebugclassfieldgetenclosingclass"></a>IDebugClassField::GetEnclosingClass
Pobiera klasę, która należy do tej klasy.

## <a name="syntax"></a>Składnia

```cpp
HRESULT GetEnclosingClass(
    IDebugClassField** ppClassField
);
```

```csharp
int GetEnclosingClass(
    out IDebugClassField ppClassField
);
```

## <a name="parameters"></a>Parametry
`ppClassField`\
określoną Zwraca obiekt [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md) reprezentujący otaczającą klasę. Zwraca wartość null, jeśli nie ma żadnej klasy otaczającej.

## <a name="return-value"></a>Wartość zwracana
Jeśli powiedzie się, zwraca S_OK; w przeciwnym razie zwraca kod błędu.

## <a name="remarks"></a>Uwagi
Jeśli klasa reprezentowana przez ten obiekt [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md) jest klasą zagnieżdżoną, `ppClassField` parametr zwraca `IDebugClassField` obiekt reprezentujący otaczającą klasę. Na przykład, uwzględniając tę definicję klasy:

```
class RootClass {
    class NestedClass { }
};
```

Wywołanie `GetEnclosingClass` metody na `IDebugClassField` obiekcie reprezentującym `NestedClass` klasę zwraca `IDebugClassField` obiekt reprezentujący klasę `RootClass` .

## <a name="see-also"></a>Zobacz też
- [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md)
