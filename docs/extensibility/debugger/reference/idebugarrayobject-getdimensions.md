---
title: IDebugArrayObject::GetDimensions | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugArrayObject::GetDimensions
helpviewer_keywords:
- IDebugArrayObject::GetDimensions method
ms.assetid: 113e0aff-9028-49d6-b104-9fe7be4772d7
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 60ee75454bf105f12b79d60e032549bcb84ab465
ms.sourcegitcommit: 77b4ca625674658d5c5766e684fa0e2a07cad4da
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/14/2019
ms.locfileid: "65615240"
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