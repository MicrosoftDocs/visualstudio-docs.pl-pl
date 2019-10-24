---
title: 'IDiaTable:: get_Count | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaTable::get_Count method
ms.assetid: bb47abe8-6706-4679-bc52-79f6444dae7e
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 9ce325c51a9dfcee32093a0a1fafe82ea6a7fdd6
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/22/2019
ms.locfileid: "72738753"
---
# <a name="idiatableget_count"></a>IDiaTable::get_Count
Pobiera liczbę elementów w tabeli.

## <a name="syntax"></a>Składnia

```C++
HRESULT get_Count ( 
   LONG* pRetVal
);
```

#### <a name="parameters"></a>Parametry
 `pRetVal`

określoną Zwraca liczbę elementów w tabeli.

## <a name="return-value"></a>Wartość zwracana
 Jeśli powiedzie się, zwraca `S_OK`; w przeciwnym razie zwraca kod błędu.

## <a name="see-also"></a>Zobacz także
- [IDiaTable](../../debugger/debug-interface-access/idiatable.md)
- [IDiaTable::Item](../../debugger/debug-interface-access/idiatable-item.md)