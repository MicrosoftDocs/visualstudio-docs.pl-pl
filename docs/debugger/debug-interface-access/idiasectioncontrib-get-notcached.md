---
title: 'IDiaSectionContrib:: get_notCached | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSectionContrib::get_notCached method
ms.assetid: 5408ea53-f64c-431e-9f62-62819026b038
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: c0c2fa26093862efb90bdfa9c5cbc54b7f59ad06
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99855404"
---
# <a name="idiasectioncontribget_notcached"></a>IDiaSectionContrib::get_notCached
Pobiera flagę wskazującą, czy nie można buforować sekcji.

## <a name="syntax"></a>Składnia

```C++
HRESULT get_notCached ( 
   BOOL* pRetVal
);
```

#### <a name="parameters"></a>Parametry
 `pRetVal`

określoną Zwraca `TRUE` czy nie można buforować sekcji; w przeciwnym razie zwraca wartość `FALSE` .

## <a name="return-value"></a>Wartość zwracana
 Jeśli powiedzie się, zwraca `S_OK` . Zwraca wartość, `S_FALSE` Jeśli ta właściwość nie jest obsługiwana. W przeciwnym razie zwraca kod błędu.

## <a name="see-also"></a>Zobacz też
- [IDiaSectionContrib](../../debugger/debug-interface-access/idiasectioncontrib.md)