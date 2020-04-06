---
title: IEEDataStorage::GetData | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEEDataStorage::GetData
helpviewer_keywords:
- IEEDataStorage::GetData
ms.assetid: 4d384039-73d4-40b4-ace6-a2474c546397
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 62a1295aeb2a6afad51dee0f1015e3ab01d13fbb
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80718211"
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
[w] Liczba bajtów do pobrania `data` (tablica musi zawierać co najmniej tę liczbę bajtów).

`sizeGotten`\
[na zewnątrz] Zwraca liczbę bajtów faktycznie pobranych.

`data`\
[w, na zewnątrz] Tablica do wypełnienia żądanymi danymi.

## <a name="return-value"></a>Wartość zwracana
 Jeśli się `S_OK`powiedzie, zwraca ; w przeciwnym razie zwraca kod błędu.

## <a name="remarks"></a>Uwagi
 Zalecanym użyciem tej metody jest pobranie wszystkich bajtów danych do tablicy lokalnej, ponieważ nie ma możliwości pominięcia bajtów w procesie pobierania. W takim przypadku `dataSize` parametr powinien być wartością zwracaną przez [Metodę GetSize.](../../../extensibility/debugger/reference/ieedatastorage-getsize.md)

## <a name="see-also"></a>Zobacz też
- [IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md)
- [GetSize](../../../extensibility/debugger/reference/ieedatastorage-getsize.md)
