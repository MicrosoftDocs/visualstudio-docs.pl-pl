---
description: Pobiera lokalizację pamięci, w której powinien być oparty obraz.
title: 'IDiaImageData:: get_imageBase | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaImageData::get_imageBase method
ms.assetid: 4ba3d9e4-b205-4ee6-a41d-6996972f1f85
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 82f80f95689a176118d5be6dcc5cfe4fdb903e0f
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/05/2021
ms.locfileid: "102148452"
---
# <a name="idiaimagedataget_imagebase"></a>IDiaImageData::get_imageBase
Pobiera lokalizację pamięci, w której powinien być oparty obraz.

## <a name="syntax"></a>Składnia

```C++
HRESULT get_imageBase ( 
   ULONGLONG* pRetVal
);
```

#### <a name="parameters"></a>Parametry
 `pRetVal`

określoną Zwraca sugerowaną wartość bazową obrazu.

## <a name="return-value"></a>Wartość zwracana
 Jeśli powiedzie się, zwraca `S_OK` ; w przeciwnym razie zwraca kod błędu.

## <a name="remarks"></a>Uwagi
 Ze względu na konflikty na podstawie obrazu można automatycznie zmienić bazę obrazu do nieużywanej lokalizacji pamięci podczas ładowania. Ta metoda zwraca wskazówkę bazową (sugerowaną lokalizację pamięci) przechowywaną w module w czasie kompilacji.

## <a name="see-also"></a>Zobacz też
- [IDiaImageData](../../debugger/debug-interface-access/idiaimagedata.md)
