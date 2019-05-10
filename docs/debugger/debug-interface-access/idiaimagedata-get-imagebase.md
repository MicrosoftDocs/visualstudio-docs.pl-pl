---
title: Idiaimagedata::get_imagebase — | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
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
ms.openlocfilehash: de8c333391530cd86c6fc66a8e6c36ce8cfecd5f
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62829058"
---
# <a name="idiaimagedatagetimagebase"></a>IDiaImageData::get_imageBase
Pobiera lokalizację pamięci, gdzie obraz powinien opierać się.

## <a name="syntax"></a>Składnia

```C++
HRESULT get_imageBase ( 
   ULONGLONG* pRetVal
);
```

#### <a name="parameters"></a>Parametry
 `pRetVal`

[out] Zwraca obraz sugerowane wartości bazowej.

## <a name="return-value"></a>Wartość zwracana
 Jeśli operacja się powiedzie, zwraca `S_OK`; w przeciwnym razie zwraca kod błędu.

## <a name="remarks"></a>Uwagi
 Z powodu konfliktów podstawowego obrazu obraz może być zmieniona automatycznie lokalizacją nieużywanej pamięci podczas jego ładowania. Ta metoda zwraca podstawowej wskazówki (lokalizacja zalecany rozmiar pamięci) są przechowywane w module w czasie kompilacji.

## <a name="see-also"></a>Zobacz też
- [IDiaImageData](../../debugger/debug-interface-access/idiaimagedata.md)