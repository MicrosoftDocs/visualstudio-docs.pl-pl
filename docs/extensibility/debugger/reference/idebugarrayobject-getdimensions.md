---
title: IDebugArrayObject::GetDimensions | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugArrayObject::GetDimensions
helpviewer_keywords:
- IDebugArrayObject::GetDimensions method
ms.assetid: 113e0aff-9028-49d6-b104-9fe7be4772d7
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 781da7eadce78d5332befe91231131f02341574b
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/29/2019
ms.locfileid: "66319005"
---
# <a name="idebugarrayobjectgetdimensions"></a>IDebugArrayObject::GetDimensions
Pobiera wymiary tablicy.

## <a name="syntax"></a>Składnia

```cpp
HRESULT GetDimensions( 
   DWORD dwCount,
   DWORD dwDimensions[]
);
```

```csharp
int GetDimensions(
   [In] uint    dwCount,
   [Out] uint[] dwDimensions
);
```

## <a name="parameters"></a>Parametry
`dwCount`\
[in] Liczba wymiarów do pobrania.

`dwDimensions`\
[out w] Tablica, która jest wypełniane rozmiarów każdego wymiaru. `dwCount` Określa maksymalny rozmiar `dwDimensions` tablicy.

## <a name="return-value"></a>Wartość zwracana
 Jeśli operacja się powiedzie, zwraca wartość S_OK; w przeciwnym razie zwraca kod błędu.

## <a name="remarks"></a>Uwagi
 Wielowymiarowe tablice może mieć różne rozmiary dla każdego wymiaru. Na przykład, biorąc pod uwagę tablicy trójwymiarowej `myarray[3][2][6]`, ta metoda zwróci 3, 2 i 6 w `dwDimensions` parametru w tej kolejności.

## <a name="see-also"></a>Zobacz także
- [IDebugArrayObject](../../../extensibility/debugger/reference/idebugarrayobject.md)