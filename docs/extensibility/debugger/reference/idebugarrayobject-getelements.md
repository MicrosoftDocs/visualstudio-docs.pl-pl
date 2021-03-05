---
description: Pobiera moduł wyliczający wszystkich elementów tablicy.
title: 'IDebugArrayObject:: GetElements | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugArrayObject::GetElements
helpviewer_keywords:
- IDebugArrayObject::GetElements method
ms.assetid: f6a6262f-5183-46ce-8a45-33ef46088b98
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 33840f3f5d5a65cf1ed929049f0b85801724a5c9
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/05/2021
ms.locfileid: "102158556"
---
# <a name="idebugarrayobjectgetelements"></a>IDebugArrayObject::GetElements
Pobiera moduł wyliczający wszystkich elementów tablicy.

## <a name="syntax"></a>Składnia

```cpp
HRESULT GetElements( 
   IEnumDebugObjects** ppEnum
);
```

```csharp
int GetElements(
   out IEnumDebugObjects ppEnum
);
```

## <a name="parameters"></a>Parametry
`ppEnum`\
określoną Zwraca obiekt [IEnumDebugObjects](../../../extensibility/debugger/reference/ienumdebugobjects.md) , który umożliwia wyliczenie wszystkich elementów.

## <a name="return-value"></a>Wartość zwracana
 Jeśli powiedzie się, zwraca S_OK; w przeciwnym razie zwraca kod błędu.

## <a name="remarks"></a>Uwagi
 Alternatywnie użyj metod [GetCount](../../../extensibility/debugger/reference/idebugarrayobject-getcount.md) i [GetElement](../../../extensibility/debugger/reference/idebugarrayobject-getelement.md) , aby wykonać iterację elementów.

## <a name="see-also"></a>Zobacz też
- [IDebugArrayObject](../../../extensibility/debugger/reference/idebugarrayobject.md)
