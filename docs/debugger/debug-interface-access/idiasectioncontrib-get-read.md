---
title: 'IDiaSectionContrib:: get_read | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSectionContrib::get_read method
ms.assetid: 68bfb35c-eabd-412a-bc8f-3094703b98c4
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: fbaac96bdb28ec1e09ede568758f87bba20ae2c2
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99855376"
---
# <a name="idiasectioncontribget_read"></a>IDiaSectionContrib::get_read
Pobiera flagę wskazującą, czy można odczytać sekcję.

## <a name="syntax"></a>Składnia

```C++
HRESULT get_read ( 
   BOOL* pRetVal
);
```

#### <a name="parameters"></a>Parametry
 `pRetVal`

określoną Zwraca `TRUE` czy można odczytać sekcję; w przeciwnym razie zwraca wartość `FALSE` .

## <a name="return-value"></a>Wartość zwracana
 Jeśli powiedzie się, zwraca `S_OK` . Zwraca wartość, `S_FALSE` Jeśli ta właściwość nie jest obsługiwana. W przeciwnym razie zwraca kod błędu.

## <a name="see-also"></a>Zobacz też
- [IDiaSectionContrib](../../debugger/debug-interface-access/idiasectioncontrib.md)