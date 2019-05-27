---
title: IDebugClassField::EnumNestedEnums | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugClassField::EnumNestedEnums
helpviewer_keywords:
- IDebugClassField::EnumNestedEnums method
ms.assetid: 90fd0cef-9145-4de6-91d4-6c881df39d6e
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 01465a0b921d61a07c4d31c8d4d4ba4b70e5bafd
ms.sourcegitcommit: 19ec963ed6d585719cb83ba677434ea6580e0d1f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/24/2019
ms.locfileid: "66206858"
---
# <a name="idebugclassfieldenumnestedenums"></a>IDebugClassField::EnumNestedEnums
Tworzy moduł wyliczający dla zagnieżdżonych moduły wyliczające tej klasy.

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
[out] Zwraca [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md) obiekt reprezentujący listę zagnieżdżonych wyliczenia. Zwraca wartość null, jeśli nie ma żadnych zagnieżdżonych wyliczenia.

## <a name="return-value"></a>Wartość zwracana
Jeśli to się powiedzie, zwraca wartość S_OK lub zwraca wartość S_FALSE, jeśli nie ma żadnych zagnieżdżonych modułów wyliczających. W przeciwnym razie zwraca kod błędu.

## <a name="remarks"></a>Uwagi
Każdy element wyliczenia jest [IDebugEnumField](../../../extensibility/debugger/reference/idebugenumfield.md) Obiekt opisujący zagnieżdżonych wyliczenia.

Wyliczenie zadeklarowane wewnątrz klasy jest traktowany jako zagnieżdżonych wyliczenia. Na przykład biorąc pod uwagę:

```
class RootClass {
    enum NestedEnum { EnumValue = 0 }
};
```

`EnumNestedEnums` Zwróci metoda [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md) obiektu, który zawiera jeden [IDebugEnumField](../../../extensibility/debugger/reference/idebugenumfield.md) obiekt, który reprezentuje `NestedEnum` wyliczenia.

## <a name="see-also"></a>Zobacz także
- [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md)
- [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)
- [IDebugEnumField](../../../extensibility/debugger/reference/idebugenumfield.md)
