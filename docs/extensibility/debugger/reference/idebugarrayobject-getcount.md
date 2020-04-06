---
title: IDebugArrayObject::GetCount | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugArrayObject::GetCount
helpviewer_keywords:
- IDebugArrayObject::GetCount method
ms.assetid: 7931f3f7-033c-4bf8-8abd-95183952ebb0
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: d9d5e322b7bcd5238335c74caa21989f1f1962ce
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80736198"
---
# <a name="idebugarrayobjectgetcount"></a>IDebugArrayObject::GetCount
Pobiera liczbę elementów w tablicy.

## <a name="syntax"></a>Składnia

```cpp
HRESULT GetCount( 
   DWORD* pdwElements
);
```

```csharp
int GetCount(
   out uint pdwElements
);
```

## <a name="parameters"></a>Parametry
`pdwElements`\
[na zewnątrz] Zwraca liczbę.

## <a name="return-value"></a>Wartość zwracana
 Jeśli się powiedzie, zwraca S_OK; w przeciwnym razie zwraca kod błędu.

## <a name="remarks"></a>Uwagi
 Ta metoda widzi wszystkie elementy obiektu tablicy jako tablicy jednowymiarowej, nawet jeśli obiekt tablicy jest wielowymiarowy. Na przykład, biorąc `myarray[3][2][6]`pod uwagę tablicę , `pdwElements` ta metoda zwróci 36 w parametrze. Użyj [GetElement](../../../extensibility/debugger/reference/idebugarrayobject-getelement.md) metody, aby pobrać poszczególne elementy po jednym na raz.

## <a name="see-also"></a>Zobacz też
- [IDebugArrayObject](../../../extensibility/debugger/reference/idebugarrayobject.md)
