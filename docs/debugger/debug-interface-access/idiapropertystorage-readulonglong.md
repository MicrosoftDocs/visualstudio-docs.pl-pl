---
title: 'IDiaPropertyStorage:: ReadULONGLONG | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaPropertyStorage::ReadULONGLONG
ms.assetid: f80a2e24-5744-4fec-bab0-3ed51aef6e58
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: b188ec5067efed410d934b98559505d48ab6585a
ms.sourcegitcommit: 66f31cc4ce1236e638ab58d2f70d3646206386fa
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/27/2020
ms.locfileid: "85466491"
---
# <a name="idiapropertystoragereadulonglong"></a>IDiaPropertyStorage::ReadULONGLONG
Odczytuje `ULONGLONG` wartości w zestawie właściwości.

## <a name="syntax"></a>Składnia

```C++
HRESULT ReadULONGLONG ( 
   PROPID     id,
   ULONGLONG* pValue
);
```

#### <a name="parameters"></a>Parametry
 `id`

podczas Identyfikator właściwości do odczytania ( `PROPID` jest zdefiniowany w WTypes. h jako `ULONG` ).

 `pValue`

określoną Zwraca wartość właściwości.

## <a name="return-value"></a>Wartość zwracana
 Jeśli to się powiedzie, zwraca `S_OK` ; w przeciwnym razie zwraca kod błędu. Zwraca `E_INVALIDARG` czy właściwość nie jest typu `ULONGLONG` .

## <a name="remarks"></a>Uwagi
 A `ULONGLONG` jest definiowana przez system Windows jako 64-bitową liczbę całkowitą bez znaku.

## <a name="see-also"></a>Zobacz też
- [IDiaPropertyStorage](../../debugger/debug-interface-access/idiapropertystorage.md)