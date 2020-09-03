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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: d804ef0caa2f6fed3ef33e64f97e51fd81e466ec
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "85466253"
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