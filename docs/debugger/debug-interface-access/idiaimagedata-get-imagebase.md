---
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 00461f73059198f5e9028658100c9ccf400be607
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "85467177"
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