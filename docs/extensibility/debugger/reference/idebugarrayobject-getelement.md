---
title: IDebugArrayObject::GetElement | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugArrayObject::GetElement
helpviewer_keywords:
- IDebugArrayObject::GetElement method
ms.assetid: 08b44341-7bf1-4a8c-8b79-98ae5785b195
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 5550a1f1e83b9343a031df39728675db07de3559
ms.sourcegitcommit: 77b4ca625674658d5c5766e684fa0e2a07cad4da
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/14/2019
ms.locfileid: "65615162"
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
[in] Indeks elementu.

`ppElement`\
[out] Zwraca [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) interfejs, który reprezentuje element.

## <a name="return-value"></a>Wartość zwracana
 Jeśli operacja się powiedzie, zwraca wartość S_OK; w przeciwnym razie zwraca kod błędu.

## <a name="remarks"></a>Uwagi
 Ta metoda uznaje wszystkie elementy obiektu tablicowego Jednowymiarowa tablica, nawet w przypadku obiektu tablicy wielowymiarowej. Na przykład, biorąc pod uwagę tablicy `myarray[3][2][6]` i `dwIndex` parametru 20, ta metoda zwróci element z `myarray[1][1][2]`, a `dwIndex` parametru 21 zwróci element z `myarray[1][1][3]`. Użyj [GetCount](../../../extensibility/debugger/reference/idebugarrayobject-getcount.md) metodę, aby określić całkowitą liczbę elementów w tablicy.

## <a name="see-also"></a>Zobacz także
- [IDebugArrayObject](../../../extensibility/debugger/reference/idebugarrayobject.md)