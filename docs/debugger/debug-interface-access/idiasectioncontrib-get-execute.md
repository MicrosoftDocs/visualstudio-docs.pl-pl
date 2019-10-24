---
title: 'IDiaSectionContrib:: get_execute | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSectionContrib::get_execute method
ms.assetid: 66eb38ce-a5e1-467e-b845-b3dc433eda91
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: f163c2a6a37dd1e379557047f70966932ef45c64
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/22/2019
ms.locfileid: "72742657"
---
# <a name="idiasectioncontribget_execute"></a>IDiaSectionContrib::get_execute
Pobiera flagę wskazującą, czy sekcja jest wykonywalna jako kod.

## <a name="syntax"></a>Składnia

```C++
HRESULT get_excute ( 
   BOOL* pRetVal
);
```

#### <a name="parameters"></a>Parametry
 `pRetVal`

określoną Zwraca `TRUE`, jeśli sekcję można wykonać jako kod; w przeciwnym razie zwraca `FALSE`.

## <a name="return-value"></a>Wartość zwracana
 Jeśli powiedzie się, zwraca `S_OK`. Zwraca `S_FALSE`, jeśli ta właściwość nie jest obsługiwana. W przeciwnym razie zwraca kod błędu.

## <a name="see-also"></a>Zobacz także
- [IDiaSectionContrib](../../debugger/debug-interface-access/idiasectioncontrib.md)