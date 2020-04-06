---
title: IDebugArrayObject::GetElement | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugArrayObject::GetElement
helpviewer_keywords:
- IDebugArrayObject::GetElement method
ms.assetid: 08b44341-7bf1-4a8c-8b79-98ae5785b195
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: e29fe09905119057224b45b455e4f56e5ce904af
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80736172"
---
# <a name="idebugarrayobjectgetelement"></a>IDebugArrayObject::GetElement
Pobiera element tablicy.

## <a name="syntax"></a>Składnia

```cpp
HRESULT GetElement( 
   DWORD          dwIndex,
   IDebugObject** ppElement
);
```

```csharp
int GetElement(
   [In] uint dwIndex,
   out IDebugObject ppElement
);
```

## <a name="parameters"></a>Parametry
`dwIndex`\
[w] Indeks elementu.

`ppElement`\
[na zewnątrz] Zwraca interfejs [IDebugObject,](../../../extensibility/debugger/reference/idebugobject.md) który reprezentuje element.

## <a name="return-value"></a>Wartość zwracana
 Jeśli się powiedzie, zwraca S_OK; w przeciwnym razie zwraca kod błędu.

## <a name="remarks"></a>Uwagi
 Ta metoda widzi wszystkie elementy obiektu tablicy jako tablicy jednowymiarowej, nawet jeśli obiekt tablicy jest wielowymiarowy. Na przykład, biorąc `myarray[3][2][6]` pod `dwIndex` uwagę tablicę i parametr 20, ta metoda zwróci element z `myarray[1][1][2]`, a `dwIndex` parametr 21 zwróci element z `myarray[1][1][3]`. Użyj [GetCount](../../../extensibility/debugger/reference/idebugarrayobject-getcount.md) metody, aby określić całkowitą liczbę elementów w tablicy.

## <a name="see-also"></a>Zobacz też
- [IDebugArrayObject](../../../extensibility/debugger/reference/idebugarrayobject.md)
