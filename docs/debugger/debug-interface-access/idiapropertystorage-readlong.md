---
title: 'IDiaPropertyStorage:: ReadLONG | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
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
ms.openlocfilehash: af9d65c571c5e0a281b968d922c9b5170bd1c561
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/22/2019
ms.locfileid: "72742891"
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

podczas Identyfikator właściwości do odczytania (`PROPID` jest zdefiniowany w WTypes. h jako `ULONG`).

 `pValue`

określoną Zwraca wartość właściwości.

## <a name="return-value"></a>Wartość zwracana
 Jeśli powiedzie się, zwraca `S_OK`; w przeciwnym razie zwraca kod błędu. Zwraca `E_INVALIDARG`, jeśli właściwość nie jest typu `LONG`.

## <a name="remarks"></a>Uwagi
 @No__t_0 jest definiowana przez system Windows jako 32-bitową liczbę całkowitą ze znakiem.

## <a name="see-also"></a>Zobacz także
- [IDiaPropertyStorage](../../debugger/debug-interface-access/idiapropertystorage.md)