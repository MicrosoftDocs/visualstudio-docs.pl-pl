---
title: IDebugClassField::GetEnclosingClass | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugClassField::GetEnclosingClass
helpviewer_keywords:
- IDebugClassField::GetEnclosingClass method
ms.assetid: a0c12e3c-9ea0-4dfb-9e45-8cea18725022
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: e5a68e32da370d6881eb2b74cbca157f7b899329
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80734390"
---
# <a name="idebugclassfieldgetenclosingclass"></a>IDebugClassField::GetEnclosingClass
Pobiera klasę, która otacza tę klasę.

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
[na zewnątrz] Zwraca obiekt [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md) reprezentujący otaczającą klasę. Zwraca wartość null, jeśli nie ma żadnej klasy otaczającej.

## <a name="return-value"></a>Wartość zwracana
Jeśli się powiedzie, zwraca S_OK; w przeciwnym razie zwraca kod błędu.

## <a name="remarks"></a>Uwagi
Jeśli klasa reprezentowana przez ten obiekt [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md) jest `ppClassField` klasą `IDebugClassField` zagnieżdżoną, parametr zwraca obiekt reprezentujący otaczającą klasę. Na przykład, biorąc pod uwagę tę definicję klasy:

```
class RootClass {
    class NestedClass { }
};
```

Wywołanie `GetEnclosingClass` metody `IDebugClassField` na obiekcie `NestedClass` reprezentującym `IDebugClassField` klasę zwraca `RootClass`obiekt reprezentujący klasę .

## <a name="see-also"></a>Zobacz też
- [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md)
