---
title: IDebugClassField::EnumBaseClasses | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugClassField::EnumBaseClasses
helpviewer_keywords:
- IDebugClassField::EnumBaseClasses method
ms.assetid: 78749674-ef75-46d3-a1f4-ff33afd90e32
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 12317c549050be31ac9e19bc7b3d8a6683f743d0
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80734476"
---
# <a name="idebugclassfieldenumbaseclasses"></a>IDebugClassField::EnumBaseClasses
Tworzy wyliczenia dla klas podstawowych tej klasy.

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

[na zewnątrz] Zwraca obiekt [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md) reprezentujący listę klas podstawowych. Zwraca wartość null, jeśli nie ma żadnych klas podstawowych.

## <a name="return-value"></a>Wartość zwracana
 Jeśli się powiedzie, zwraca S_OK, zwraca S_SH_NO_BASE_CLASSES, jeśli nie ma `ppEnum` żadnych klas podstawowych (a parametr jest ustawiony na wartość null); w przeciwnym razie zwraca kod błędu.

## <a name="remarks"></a>Uwagi
 Klasy podstawowe w obiekcie wyliczacza są określone w kolejności najbardziej natychmiastowe (lub najbardziej pochodne) klasy podstawowej do najbardziej zdalnej klasy podstawowej. Na przykład biorąc pod uwagę klasy C++:

```
class Root { }
class Level1 : Root { }
class Level2 : Level1 { }
class MyClass : Level2 { }
```

 Wyliczenie spowoduje zwrócenie klas podstawowych `Level2` `Level1`w `Root`kolejności , .

## <a name="see-also"></a>Zobacz też
- [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md)
- [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)
