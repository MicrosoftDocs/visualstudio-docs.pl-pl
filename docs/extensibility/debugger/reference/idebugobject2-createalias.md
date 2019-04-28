---
title: IDebugObject2::CreateAlias | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugObject2::CreateAlias
helpviewer_keywords:
- IDebugObject2::CreateAlias method
ms.assetid: 54a05920-5d13-4f67-962b-d1a7f013dff9
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 226d584a2773a342b8247ff337e686be2da6bf9b
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62843038"
---
# <a name="idebugobject2createalias"></a>IDebugObject2::CreateAlias
Tworzy unikatowy identyfikator lub alias dla tego obiektu lub zwraca istniejącego aliasu.

## <a name="syntax"></a>Składnia

```cpp
HRESULT CreateAlias(
   IDebugAlias** ppAlias
);
```

```csharp
int CreateAlias(
   out IDebugAlias ppAlias
);
```

#### <a name="parameters"></a>Parametry
 `ppAlias`

 [out] Alias nowa (lub istniejąca).

## <a name="return-value"></a>Wartość zwracana
 Jeśli operacja się powiedzie, zwraca wartość S_OK; w przeciwnym razie zwraca kod błędu.

## <a name="remarks"></a>Uwagi
 Alias jest etykietę, która reprezentuje określonego obiektu, gdy obiekt jest w pamięci.

## <a name="see-also"></a>Zobacz też
- [IDebugObject2](../../../extensibility/debugger/reference/idebugobject2.md)
- [IDebugAlias](../../../extensibility/debugger/reference/idebugalias.md)