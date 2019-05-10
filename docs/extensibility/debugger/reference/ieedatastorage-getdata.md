---
title: IEEDataStorage::GetData | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEEDataStorage::GetData
helpviewer_keywords:
- IEEDataStorage::GetData
ms.assetid: 4d384039-73d4-40b4-ace6-a2474c546397
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 8d9c00f21ab39d5785acb0090b16b5b1fc193699
ms.sourcegitcommit: 6196d0b7fdcb08ba6d28a8151ad36b8d1139f2cc
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2019
ms.locfileid: "65224192"
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

 [in] Liczba bajtów do pobrania ( `data` tablicy musi posiadać co najmniej tej liczby bajtów).

 `sizeGotten`\

 [out] Zwraca liczbę bajtów, które rzeczywiście zostały pobrane.

 `data`\

 [out w] Tablica do wypełniona żądanych danych.

## <a name="return-value"></a>Wartość zwracana
 Jeśli operacja się powiedzie, zwraca `S_OK`; w przeciwnym razie zwraca kod błędu.

## <a name="remarks"></a>Uwagi
 Zalecane użycie tej metody jest do pobrania wszystkich bajtów danych do lokalnej tablicy, ponieważ nie istnieje żaden sposób na pominięcie nad bajtów w procesie pobierania. W tym przypadku parametr `dataSize` powinien mieć wartość zwracana przez [getsize —](../../../extensibility/debugger/reference/ieedatastorage-getsize.md) metody.

## <a name="see-also"></a>Zobacz także
- [IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md)
- [GetSize](../../../extensibility/debugger/reference/ieedatastorage-getsize.md)