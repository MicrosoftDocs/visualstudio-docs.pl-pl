---
title: 'IDiaTable:: get_name | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaTable::get_name method
ms.assetid: f6e9cd07-63cd-48a6-9835-e69c2d0859c5
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: e3874ad63026208d096a2b7866377d09ac79cbe9
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/22/2019
ms.locfileid: "72738759"
---
# <a name="idiatableget_name"></a>IDiaTable::get_name
Pobiera nazwę tabeli.

## <a name="syntax"></a>Składnia

```C++
HRESULT get_name ( 
   BSTR* pRetVal
);
```

#### <a name="parameters"></a>Parametry
 `pRetVal`

określoną Zwraca nazwę tabeli.

## <a name="return-value"></a>Wartość zwracana
 Jeśli powiedzie się, zwraca `S_OK`; w przeciwnym razie zwraca kod błędu.

## <a name="see-also"></a>Zobacz także
- [IDiaTable](../../debugger/debug-interface-access/idiatable.md)