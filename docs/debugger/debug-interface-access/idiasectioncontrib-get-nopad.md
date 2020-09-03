---
title: 'IDiaSectionContrib:: get_nopad | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSectionContrib::get_nopad method
ms.assetid: f5c08603-0b3e-4e81-acf1-1b95a6a83bed
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 6b27189b27fef22a3fe5b3926ded324e75081547
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "85466218"
---
# <a name="idiasectioncontribget_nopad"></a>IDiaSectionContrib::get_nopad
Pobiera flagę wskazującą, czy sekcja nie powinna być uzupełniona do następnej granicy pamięci.

## <a name="syntax"></a>Składnia

```C++
HRESULT get_nopad(
   BOOL* pRetVal
};
```

#### <a name="parameters"></a>Parametry
 `pRetVal`

określoną Zwraca `TRUE` czy sekcja nie powinna być uzupełniona do następnej granicy pamięci; w przeciwnym razie zwraca `FALSE` .

## <a name="return-value"></a>Wartość zwracana
 Jeśli powiedzie się, zwraca `S_OK` . Zwraca wartość, `S_FALSE` Jeśli ta właściwość nie jest obsługiwana. W przeciwnym razie zwraca kod błędu.

## <a name="remarks"></a>Uwagi
 Jest to właściwość zwykle widoczna tylko dla starszych plików.

## <a name="see-also"></a>Zobacz też
- [IDiaSectionContrib](../../debugger/debug-interface-access/idiasectioncontrib.md)