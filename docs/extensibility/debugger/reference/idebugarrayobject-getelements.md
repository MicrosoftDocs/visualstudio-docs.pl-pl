---
title: IDebugArrayObject::GetElements | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugArrayObject::GetElements
helpviewer_keywords:
- IDebugArrayObject::GetElements method
ms.assetid: f6a6262f-5183-46ce-8a45-33ef46088b98
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: be06acbef93d8858557fea5bd7563168be2d28aa
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80736238"
---
# <a name="idebugarrayobjectgetelements"></a>IDebugArrayObject::GetElements
Pobiera wyliczacza wszystkich elementów tablicy.

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
[na zewnątrz] Zwraca [obiekt IEnumDebugObjects,](../../../extensibility/debugger/reference/ienumdebugobjects.md) który umożliwia wyliczanie wszystkich elementów.

## <a name="return-value"></a>Wartość zwracana
 Jeśli się powiedzie, zwraca S_OK; w przeciwnym razie zwraca kod błędu.

## <a name="remarks"></a>Uwagi
 Alternatywnie należy użyć [GetCount](../../../extensibility/debugger/reference/idebugarrayobject-getcount.md) i [GetElement](../../../extensibility/debugger/reference/idebugarrayobject-getelement.md) metody do iteracji za pośrednictwem elementów.

## <a name="see-also"></a>Zobacz też
- [IDebugArrayObject](../../../extensibility/debugger/reference/idebugarrayobject.md)
