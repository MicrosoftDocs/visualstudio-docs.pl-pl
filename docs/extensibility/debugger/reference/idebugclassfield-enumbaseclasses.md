---
title: IDebugClassField::EnumBaseClasses | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugClassField::EnumBaseClasses
helpviewer_keywords:
- IDebugClassField::EnumBaseClasses method
ms.assetid: 78749674-ef75-46d3-a1f4-ff33afd90e32
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 74889ed04dceb133c80467d20f723f9561b6e25c
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/22/2019
ms.locfileid: "56703828"
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

#### <a name="parameters"></a>Parametry
 `ppEnum`

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

## <a name="see-also"></a>Zobacz też
- [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md)
- [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)