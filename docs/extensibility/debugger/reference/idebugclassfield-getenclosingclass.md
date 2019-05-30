---
title: IDebugClassField::GetEnclosingClass | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugClassField::GetEnclosingClass
helpviewer_keywords:
- IDebugClassField::GetEnclosingClass method
ms.assetid: a0c12e3c-9ea0-4dfb-9e45-8cea18725022
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 6927a63241e2f2794fb5c70945962e00a1676431
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/29/2019
ms.locfileid: "66329496"
---
# <a name="idebugclassfieldgetenclosingclass"></a>IDebugClassField::GetEnclosingClass
Pobiera klasę, która otacza tej klasy.

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
[out] Zwraca [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md) obiekt reprezentujący otaczającej klasy. Zwraca wartość null, jeśli nie otaczającej klasy.

## <a name="return-value"></a>Wartość zwracana
Jeśli operacja się powiedzie, zwraca wartość S_OK; w przeciwnym razie zwraca kod błędu.

## <a name="remarks"></a>Uwagi
Jeśli klasa reprezentowany przez ten [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md) obiekt jest klasy zagnieżdżonej, a następnie `ppClassField` parametr zwraca `IDebugClassField` obiekt reprezentujący otaczającej klasy. Na przykład biorąc pod uwagę tę definicję klasy:

```
class RootClass {
    class NestedClass { }
};
```

Wywoływanie `GetEnclosingClass` metody `IDebugClassField` obiekt reprezentujący `NestedClass` klasy zwraca `IDebugClassField` obiekt reprezentujący klasę `RootClass`.

## <a name="see-also"></a>Zobacz także
- [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md)
