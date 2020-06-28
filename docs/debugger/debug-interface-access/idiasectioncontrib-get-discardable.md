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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 1adb64767baa61e8c48739df93808aeac22266bb
ms.sourcegitcommit: 66f31cc4ce1236e638ab58d2f70d3646206386fa
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/27/2020
ms.locfileid: "85466267"
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