---
title: IDebugClassField::EnumBaseClasses | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugClassField::EnumBaseClasses
helpviewer_keywords:
- IDebugClassField::EnumBaseClasses method
ms.assetid: 78749674-ef75-46d3-a1f4-ff33afd90e32
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: f5735ac6f0ecdf9d3f2a0e3bb868be092b8fdb7e
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/29/2019
ms.locfileid: "66349651"
---
# <a name="idebugclassfieldenumbaseclasses"></a>IDebugClassField::EnumBaseClasses
Tworzy moduł wyliczający dla klasy bazowe tej klasy.

## <a name="syntax"></a>Składnia

```cpp
HRESULT EnumBaseClasses( 
   IEnumDebugFields** ppEnum
);
```

```csharp
int EnumBaseClasses(
   out IEnumDebugFields ppEnum
);
```

## <a name="parameters"></a>Parametry
`ppEnum`\

[out] Zwraca [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md) obiekt reprezentujący listę klas bazowych. Zwraca wartość null, jeśli nie mają klas bazowych.

## <a name="return-value"></a>Wartość zwracana
 Jeśli to się powiedzie, zwraca wartość S_OK, funkcja zwraca S_SH_NO_BASE_CLASSES, jeśli nie mają klas bazowych (i `ppEnum` parametr jest ustawiony na wartość null); w przeciwnym razie zwraca kod błędu.

## <a name="remarks"></a>Uwagi
 Klasy bazowe w obiekcie moduł wyliczający są określone w kolejności od najbardziej bezpośredni (lub najbardziej pochodnej) klasy bazowej do klasy bazowej najbardziej zdalnego. Na przykład biorąc klasy C++:

```
class Root { }
class Level1 : Root { }
class Level2 : Level1 { }
class MyClass : Level2 { }
```

 Wyliczanie zwróci bazowe klasy w kolejności `Level2`, `Level1`, `Root`.

## <a name="see-also"></a>Zobacz także
- [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md)
- [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)