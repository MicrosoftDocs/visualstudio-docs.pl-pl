---
title: 'IDiaSectionContrib:: get_informational | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSectionContrib::get_informational method
ms.assetid: 5351e89f-7db1-4f8e-9e57-2dd1c74002e0
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 8801a6ca7e2284afeed19e2519003ead1288f0e3
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99855432"
---
# <a name="idiasectioncontribget_informational"></a>IDiaSectionContrib::get_informational
Pobiera flagę wskazującą, czy sekcja zawiera komentarze lub podobne informacje.

## <a name="syntax"></a>Składnia

```C++
HRESULT get_informational(
   BOOL* pRetVal
};
```

#### <a name="parameters"></a>Parametry
 `pRetVal`

określoną Zwraca `TRUE` czy sekcja zawiera komentarze lub inne informacje; w przeciwnym razie zwraca `FALSE` .

## <a name="return-value"></a>Wartość zwracana
 Jeśli powiedzie się, zwraca `S_OK` . Zwraca wartość, `S_FALSE` Jeśli ta właściwość nie jest obsługiwana. W przeciwnym razie zwraca kod błędu.

## <a name="remarks"></a>Uwagi
 Zazwyczaj sekcja. dyrektywa zawiera informacje.

## <a name="see-also"></a>Zobacz też
- [IDiaSectionContrib](../../debugger/debug-interface-access/idiasectioncontrib.md)