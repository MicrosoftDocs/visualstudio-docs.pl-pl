---
title: 'IDebugArrayObject:: GetDimensions | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugArrayObject::GetDimensions
helpviewer_keywords:
- IDebugArrayObject::GetDimensions method
ms.assetid: 113e0aff-9028-49d6-b104-9fe7be4772d7
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 2c0c71032fc8f5c75522f6b1f9e0d8cb1308f63f
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99870197"
---
# <a name="idebugarrayobjectgetdimensions"></a>IDebugArrayObject::GetDimensions
Pobiera Wymiary tablicy.

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
podczas Liczba wymiarów do pobrania.

`dwDimensions`\
[in. out] Tablica, która jest wypełniana rozmiarem każdego wymiaru. `dwCount` Określa maksymalny rozmiar `dwDimensions` tablicy.

## <a name="return-value"></a>Wartość zwracana
 Jeśli powiedzie się, zwraca S_OK; w przeciwnym razie zwraca kod błędu.

## <a name="remarks"></a>Uwagi
 Tablica wielowymiarowa może mieć różne rozmiary dla każdego wymiaru. Na przykład w przypadku tablicy trójwymiarowej `myarray[3][2][6]` Ta metoda zwróci 3, 2 i 6 w `dwDimensions` parametrze w tej kolejności.

## <a name="see-also"></a>Zobacz też
- [IDebugArrayObject](../../../extensibility/debugger/reference/idebugarrayobject.md)
