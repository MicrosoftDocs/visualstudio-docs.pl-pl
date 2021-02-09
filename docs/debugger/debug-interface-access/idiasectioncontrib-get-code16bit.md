---
title: 'IDiaSectionContrib:: get_code16bit | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSectionContrib::get_code16bit method
ms.assetid: 8cde8fc5-9546-4f82-b4a8-afd0d835039e
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 82f074bc03e8c893b2f9a03d185056c34f0ceb28
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99864524"
---
# <a name="idiasectioncontribget_code16bit"></a>IDiaSectionContrib::get_code16bit
Pobiera flagę wskazującą, czy sekcja zawiera kod 16-bitowy.

## <a name="syntax"></a>Składnia

```C++
HRESULT get_code16bit(
   BOOL *pRetVal
};
```

#### <a name="parameters"></a>Parametry
 `pRetVal`

określoną Zwraca `TRUE` czy kod w sekcji jest 16-bitowy; w przeciwnym razie zwraca `FALSE` .

## <a name="return-value"></a>Wartość zwracana
 Jeśli powiedzie się, zwraca `S_OK` ; w przeciwnym razie zwraca kod błędu.

## <a name="remarks"></a>Uwagi
 Ta metoda wskazuje tylko, czy kod jest 16-bitowy. Jeśli kod nie jest 16-bitowy, może to być coś innego, takiego jak 32-bitowy lub 64-bitowy kod.

## <a name="see-also"></a>Zobacz też
- [IDiaSectionContrib](../../debugger/debug-interface-access/idiasectioncontrib.md)