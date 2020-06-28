---
title: 'IDiaPropertyStorage:: ReadLONG | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaPropertyStorage::ReadLONG
ms.assetid: 32054cbc-db55-4513-a1b4-de80e77aac8a
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 697d93af1256d76e5448de5cbc34e04ffc26927f
ms.sourcegitcommit: 66f31cc4ce1236e638ab58d2f70d3646206386fa
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/27/2020
ms.locfileid: "85466582"
---
# <a name="idiapropertystoragereadlong"></a>IDiaPropertyStorage::ReadLONG
Odczytuje `LONG` wartości w zestawie właściwości.

## <a name="syntax"></a>Składnia

```C++
HRESULT ReadDLONG ( 
   PROPID id,
   LONG*  pValue
);
```

#### <a name="parameters"></a>Parametry
 `id`

podczas Identyfikator właściwości do odczytania ( `PROPID` jest zdefiniowany w WTypes. h jako `ULONG` ).

 `pValue`

określoną Zwraca wartość właściwości.

## <a name="return-value"></a>Wartość zwracana
 Jeśli to się powiedzie, zwraca `S_OK` ; w przeciwnym razie zwraca kod błędu. Zwraca `E_INVALIDARG` czy właściwość nie jest typu `LONG` .

## <a name="remarks"></a>Uwagi
 A `LONG` jest definiowana przez system Windows jako 32-bitową liczbę całkowitą ze znakiem.

## <a name="see-also"></a>Zobacz też
- [IDiaPropertyStorage](../../debugger/debug-interface-access/idiapropertystorage.md)