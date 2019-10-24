---
title: 'IDiaLineNumber:: get_compilandId | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaLineNumber::get_compilandId method
ms.assetid: 2cd6f551-8091-47c7-803f-3f79a766a211
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 9ab4776029f13a68746a6b4d6ca0343450f477a9
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/22/2019
ms.locfileid: "72743217"
---
# <a name="idialinenumberget_compilandid"></a>IDiaLineNumber::get_compilandId
Pobiera unikatowy identyfikator jednostka kompilacji, który przyczynia się do tego wiersza.

## <a name="syntax"></a>Składnia

```C++
HRESULT get_compilandId ( 
   DWORD* pRetVal
);
```

#### <a name="parameters"></a>Parametry
 `pRetVal`

określoną Zwraca `DWORD`, która zawiera unikatowy identyfikator jednostka kompilacji, który współtworzył ten wiersz.

## <a name="return-value"></a>Wartość zwracana
 Jeśli powiedzie się, zwraca `S_OK`. Zwraca `S_FALSE`, jeśli ta właściwość nie jest obsługiwana. W przeciwnym razie zwraca kod błędu.

## <a name="see-also"></a>Zobacz także
- [IDiaLineNumber](../../debugger/debug-interface-access/idialinenumber.md)