---
title: IDebugClassField::EnumNestedEnums | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugClassField::EnumNestedEnums
helpviewer_keywords:
- IDebugClassField::EnumNestedEnums method
ms.assetid: 90fd0cef-9145-4de6-91d4-6c881df39d6e
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 38ee3ccd1ffd3130bc918da18c631cf08683f064
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80734411"
---
# <a name="idebugclassfieldenumnestedenums"></a>IDebugClassField::EnumNestedEnums
Tworzy wyliczenia dla zagnieżdżonych wyliczników tej klasy.

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
[na zewnątrz] Zwraca obiekt [IEnumDebugFields reprezentujący](../../../extensibility/debugger/reference/ienumdebugfields.md) listę zagnieżdżonych wyliczeń. Zwraca wartość null, jeśli nie ma żadnych zagnieżdżonych wyliczenia.

## <a name="return-value"></a>Wartość zwracana
Jeśli się powiedzie, zwraca S_OK lub zwraca S_FALSE, jeśli nie ma żadnych zagnieżdżonych wyliczników. W przeciwnym razie zwraca kod błędu.

## <a name="remarks"></a>Uwagi
Każdy element wyliczenia jest [IDebugEnumField](../../../extensibility/debugger/reference/idebugenumfield.md) obiektu opisujące zagnieżdżone wyliczenie.

Wyliczenie zadeklarowane wewnątrz klasy jest uważane za zagnieżdżone wyliczenie. Na przykład podane:

```
class RootClass {
    enum NestedEnum { EnumValue = 0 }
};
```

Metoda `EnumNestedEnums` zwróci [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md) obiektu, który zawiera jeden [IDebugEnumField](../../../extensibility/debugger/reference/idebugenumfield.md) obiektu, który reprezentuje wyliczenie. `NestedEnum`

## <a name="see-also"></a>Zobacz też
- [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md)
- [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)
- [IDebugEnumField](../../../extensibility/debugger/reference/idebugenumfield.md)
