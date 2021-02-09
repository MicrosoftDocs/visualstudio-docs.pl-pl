---
title: 'IDebugClassField:: EnumNestedClasses | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugClassField::EnumNestedClasses
helpviewer_keywords:
- IDebugClassField::EnumNestedClasses method
ms.assetid: 2ba5ef0c-395e-4006-9e3c-9b06e1d711d0
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 63b42df8181ca12da1be2aca6faf1346406b621f
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99877437"
---
# <a name="idebugclassfieldenumnestedclasses"></a>IDebugClassField::EnumNestedClasses
Tworzy moduł wyliczający dla klas zagnieżdżonych w tej klasie.

## <a name="syntax"></a>Składnia

```cpp
HRESULT EnumNestedClasses(
    IEnumDebugFields** ppEnum
);
```

```csharp
int EnumNestedClasses(
    out IEnumDebugFields ppEnum
);
```

## <a name="parameters"></a>Parametry
`ppEnum`\
określoną Zwraca obiekt [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md) reprezentujący listę klas zagnieżdżonych. Zwraca wartość null, jeśli nie ma klas zagnieżdżonych.

## <a name="return-value"></a>Wartość zwracana
Jeśli to się powiedzie, zwraca S_OK lub zwraca S_FALSE, jeśli nie ma żadnych zagnieżdżonych klas. W przeciwnym razie zwraca kod błędu.

## <a name="remarks"></a>Uwagi
Każdy element wyliczenia jest obiektem [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md) , opisującym klasę zagnieżdżoną.

Klasa zagnieżdżona jest klasą zdefiniowaną wewnątrz innej klasy. Na przykład:

```
class RootClass {
   class NestedClass { }
};
```

Wyliczenie [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md) będzie zawierać jeden obiekt reprezentujący `NestedClass` klasę.

## <a name="see-also"></a>Zobacz też
- [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md)
- [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)
