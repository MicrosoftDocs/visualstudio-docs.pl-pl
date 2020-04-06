---
title: IDebugClassField::EnumNestedClasses | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugClassField::EnumNestedClasses
helpviewer_keywords:
- IDebugClassField::EnumNestedClasses method
ms.assetid: 2ba5ef0c-395e-4006-9e3c-9b06e1d711d0
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 3e6ef918b55d8b311380264d688085b0d2803601
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80734431"
---
# <a name="idebugclassfieldenumnestedclasses"></a>IDebugClassField::EnumNestedClasses
Tworzy wyliczenie dla klas zagnieżdżonych w tej klasie.

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
[na zewnątrz] Zwraca obiekt [IEnumDebugFields reprezentujący](../../../extensibility/debugger/reference/ienumdebugfields.md) listę klas zagnieżdżonych. Zwraca wartość null, jeśli nie ma żadnych klas zagnieżdżonych.

## <a name="return-value"></a>Wartość zwracana
Jeśli się powiedzie, zwraca S_OK lub zwraca S_FALSE, jeśli nie ma żadnych klas zagnieżdżonych. W przeciwnym razie zwraca kod błędu.

## <a name="remarks"></a>Uwagi
Każdy element wyliczenia jest [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md) obiektu opisujące klasy zagnieżdżonej.

Klasa zagnieżdżona jest klasą zdefiniowaną wewnątrz innej klasy. Przykład:

```
class RootClass {
   class NestedClass { }
};
```

[Wyliczenie IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md) będzie zawierać jeden `NestedClass` obiekt reprezentujący klasę.

## <a name="see-also"></a>Zobacz też
- [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md)
- [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)
