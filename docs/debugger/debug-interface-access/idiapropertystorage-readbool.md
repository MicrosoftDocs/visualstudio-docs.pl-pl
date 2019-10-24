---
title: 'IDiaPropertyStorage:: ReadBOOL | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaPropertyStorage::ReadBOOL
ms.assetid: ad1822db-4572-48f7-9919-f8137f6701f2
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: d776e37bab189e61d0264f4cbda24f89cb4501ce
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/22/2019
ms.locfileid: "72742936"
---
# <a name="idiapropertystoragereadbool"></a>IDiaPropertyStorage::ReadBOOL
Odczytuje `BOOL` wartości w zestawie właściwości.

## <a name="syntax"></a>Składnia

```C++
HRESULT ReadBOOL ( 
   PROPID id,
   BOOL*  pValue
);
```

#### <a name="parameters"></a>Parametry
 `id`

podczas Identyfikator właściwości do odczytania (`PROPID` jest zdefiniowany w WTypes. h jako `ULONG`).

 `pValue`

określoną Zwraca wartość właściwości.

## <a name="return-value"></a>Wartość zwracana
 Jeśli powiedzie się, zwraca `S_OK`; w przeciwnym razie zwraca kod błędu. Zwraca `E_INVALIDARG`, jeśli właściwość nie jest typu `BOOL`.

## <a name="remarks"></a>Uwagi
 Aby zapewnić spójne wyniki, interpretuj wartość `BOOL`, tak aby wartości niezerowe były `TRUE` i zero jest `FALSE`.

## <a name="see-also"></a>Zobacz także
- [IDiaPropertyStorage](../../debugger/debug-interface-access/idiapropertystorage.md)