---
title: 'IDiaPropertyStorage:: ReadBSTR | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaPropertyStorage::ReadBSTR
ms.assetid: 7214643b-3286-48ed-90aa-0fe95b4cae5b
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: ef0b5bac11a1bf3da7e8081f7ae24b6a7a6f1a71
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/22/2019
ms.locfileid: "72742918"
---
# <a name="idiapropertystoragereadbstr"></a>IDiaPropertyStorage::ReadBSTR
Odczytuje `BSTR` wartości w zestawie właściwości.

## <a name="syntax"></a>Składnia

```C++
HRESULT ReadBSTR ( 
   PROPID id,
   BSTR*  pValue
);
```

#### <a name="parameters"></a>Parametry
 `id`

podczas Identyfikator właściwości do odczytania (`PROPID` jest zdefiniowany w WTypes. h jako `ULONG`).

 `pValue`

określoną Zwraca wartość właściwości.

## <a name="return-value"></a>Wartość zwracana
 Jeśli powiedzie się, zwraca `S_OK`; w przeciwnym razie zwraca kod błędu. Zwraca `E_INVALIDARG`, jeśli właściwość nie jest typu `BSTR`.

## <a name="remarks"></a>Uwagi
 @No__t_0 jest definiowana przez system Windows jako ciąg znaków dwubajtowych zakończony zerem.

## <a name="see-also"></a>Zobacz także
- [IDiaPropertyStorage](../../debugger/debug-interface-access/idiapropertystorage.md)