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
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 182185c36c57bde8d6140644a528bb432608c2bc
ms.sourcegitcommit: 77b4ca625674658d5c5766e684fa0e2a07cad4da
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/14/2019
ms.locfileid: "65615266"
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
[out] Zwraca liczbę.

## <a name="return-value"></a>Wartość zwracana
 Jeśli operacja się powiedzie, zwraca wartość S_OK; w przeciwnym razie zwraca kod błędu.

## <a name="remarks"></a>Uwagi
 Ta metoda uznaje wszystkie elementy obiektu tablicowego Jednowymiarowa tablica, nawet w przypadku obiektu tablicy wielowymiarowej. Na przykład, biorąc pod uwagę tablicy `myarray[3][2][6]`, ta metoda zwróci 36 w `pdwElements` parametru. Użyj [GetElement](../../../extensibility/debugger/reference/idebugarrayobject-getelement.md) metodę, aby pobrać poszczególne elementy jednego naraz.

## <a name="see-also"></a>Zobacz także
- [IDebugArrayObject](../../../extensibility/debugger/reference/idebugarrayobject.md)