---
title: IDebugClassField::GetEnclosingClass | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IDebugClassField::GetEnclosingClass
helpviewer_keywords:
- IDebugClassField::GetEnclosingClass method
ms.assetid: a0c12e3c-9ea0-4dfb-9e45-8cea18725022
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 6ab5be03fc6421f03742878f2b72f568ec0915dc
ms.sourcegitcommit: 7153e2fc717d32e0e9c8a9b8c406dc4053c9fd53
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/19/2019
ms.locfileid: "56412919"
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

#### <a name="parameters"></a>Parametry
`ppClassField`  
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

## <a name="see-also"></a>Zobacz też
[IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md)
