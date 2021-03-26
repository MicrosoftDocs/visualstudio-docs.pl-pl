---
description: Tworzy moduł wyliczający dla zagnieżdżonych modułów wyliczających tej klasy.
title: 'IDebugClassField:: EnumNestedEnums | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugClassField::EnumNestedEnums
helpviewer_keywords:
- IDebugClassField::EnumNestedEnums method
ms.assetid: 90fd0cef-9145-4de6-91d4-6c881df39d6e
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: b2e0d908c88b82e9ed706ab919050e1f4943df0c
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/25/2021
ms.locfileid: "105088565"
---
# <a name="idebugclassfieldenumnestedenums"></a>IDebugClassField::EnumNestedEnums
Tworzy moduł wyliczający dla zagnieżdżonych modułów wyliczających tej klasy.

## <a name="syntax"></a>Składnia

```cpp
HRESULT EnumNestedEnums(
    IEnumDebugFields** ppEnum
);
```

```csharp
int EnumNestedEnums(
    out IEnumDebugFields ppEnum
);
```

## <a name="parameters"></a>Parametry
`ppEnum`\
określoną Zwraca obiekt [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md) reprezentujący listę zagnieżdżonych wyliczeń. Zwraca wartość null, jeśli nie ma żadnych zagnieżdżonych wyliczeń.

## <a name="return-value"></a>Wartość zwracana
Jeśli to się powiedzie, zwraca S_OK lub zwraca S_FALSE, jeśli nie ma zagnieżdżonych modułów wyliczających. W przeciwnym razie zwraca kod błędu.

## <a name="remarks"></a>Uwagi
Każdy element wyliczenia jest obiektem [IDebugEnumField](../../../extensibility/debugger/reference/idebugenumfield.md) opisującym Wyliczenie zagnieżdżone.

Wyliczenie zadeklarowane wewnątrz klasy jest uznawane za zagnieżdżone Wyliczenie. Na przykład:

```
class RootClass {
    enum NestedEnum { EnumValue = 0 }
};
```

`EnumNestedEnums`Metoda zwróci obiekt [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md) , który zawiera jeden obiekt [IDebugEnumField](../../../extensibility/debugger/reference/idebugenumfield.md) , który reprezentuje `NestedEnum` Wyliczenie.

## <a name="see-also"></a>Zobacz też
- [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md)
- [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)
- [IDebugEnumField](../../../extensibility/debugger/reference/idebugenumfield.md)
