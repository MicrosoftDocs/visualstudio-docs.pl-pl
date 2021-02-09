---
title: 'IDiaSectionContrib:: get_discardable | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSectionContrib::get_discardable method
ms.assetid: 30ca88d4-3198-4b0f-b30e-2e54b3607fe9
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 2754a7eb04701c70fdc54c1f41ac8d673b1bd4af
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99855453"
---
# <a name="idiasectioncontribget_discardable"></a>IDiaSectionContrib::get_discardable
Pobiera flagę wskazującą, czy sekcja może zostać odrzucona.

## <a name="syntax"></a>Składnia

```C++
HRESULT get_discardable ( 
   BOOL* pRetVal
);
```

#### <a name="parameters"></a>Parametry
 `pRetVal`

określoną Zwraca `TRUE` czy sekcja może zostać odrzucona z pamięci w razie konieczności; w przeciwnym razie zwraca `FALSE` .

## <a name="return-value"></a>Wartość zwracana
 Jeśli powiedzie się, zwraca `S_OK` . Zwraca wartość, `S_FALSE` Jeśli ta właściwość nie jest obsługiwana. W przeciwnym razie zwraca kod błędu.

## <a name="see-also"></a>Zobacz też
- [IDiaSectionContrib](../../debugger/debug-interface-access/idiasectioncontrib.md)