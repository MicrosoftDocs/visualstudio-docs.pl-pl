---
title: IDebugArrayObject::GetCount | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugArrayObject::GetCount
helpviewer_keywords:
- IDebugArrayObject::GetCount method
ms.assetid: 7931f3f7-033c-4bf8-8abd-95183952ebb0
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 30419e20b6ac1519e3d9b278aabfcb012372d193
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/22/2019
ms.locfileid: "56715014"
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

#### <a name="parameters"></a>Parametry
 `pdwElements`

 [out] Zwraca liczbę.

## <a name="return-value"></a>Wartość zwracana
 Jeśli operacja się powiedzie, zwraca wartość S_OK; w przeciwnym razie zwraca kod błędu.

## <a name="remarks"></a>Uwagi
 Ta metoda uznaje wszystkie elementy obiektu tablicowego Jednowymiarowa tablica, nawet w przypadku obiektu tablicy wielowymiarowej. Na przykład, biorąc pod uwagę tablicy `myarray[3][2][6]`, ta metoda zwróci 36 w `pdwElements` parametru. Użyj [GetElement](../../../extensibility/debugger/reference/idebugarrayobject-getelement.md) metodę, aby pobrać poszczególne elementy jednego naraz.

## <a name="see-also"></a>Zobacz też
- [IDebugArrayObject](../../../extensibility/debugger/reference/idebugarrayobject.md)