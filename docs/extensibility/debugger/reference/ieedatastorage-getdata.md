---
description: Pobiera określoną liczbę bajtów z obiektu.
title: 'IEEDataStorage:: GetData | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEEDataStorage::GetData
helpviewer_keywords:
- IEEDataStorage::GetData
ms.assetid: 4d384039-73d4-40b4-ace6-a2474c546397
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 218ffea2d35f34768550938e8bdc4c087bb3a2cf
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/25/2021
ms.locfileid: "105083547"
---
# <a name="ieedatastoragegetdata"></a>IEEDataStorage::GetData
Pobiera określoną liczbę bajtów z obiektu.

## <a name="syntax"></a>Składnia

```cpp
HRESULT GetData(
   ULONG  dataSize,
   ULONG* sizeGotten,
   BYTE*  data
);
```

```csharp
int GetData(
   uint     dataSize,
   out uint sizeGotten,
   byte[]   data
);
```

## <a name="parameters"></a>Parametry
`dataSize`\
podczas Liczba bajtów do pobrania ( `data` Tablica musi zawierać co najmniej następującą liczbę bajtów).

`sizeGotten`\
określoną Zwraca liczbę bajtów pobieranych w rzeczywistości.

`data`\
[in. out] Tablica, która ma zostać wypełniona dla żądanych danych.

## <a name="return-value"></a>Wartość zwracana
 Jeśli powiedzie się, zwraca `S_OK` ; w przeciwnym razie zwraca kod błędu.

## <a name="remarks"></a>Uwagi
 Zalecanym zastosowaniem tej metody jest pobranie wszystkich bajtów danych do tablicy lokalnej, ponieważ nie ma możliwości pomijania bajtów w procesie pobierania. W tym przypadku parametr `dataSize` powinien być wartością zwracaną przez metodę [GetSize](../../../extensibility/debugger/reference/ieedatastorage-getsize.md) .

## <a name="see-also"></a>Zobacz też
- [IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md)
- [GetSize —](../../../extensibility/debugger/reference/ieedatastorage-getsize.md)
