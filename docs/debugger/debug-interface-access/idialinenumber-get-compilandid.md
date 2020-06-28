---
title: 'IDiaLineNumber:: get_compilandId | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
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
ms.openlocfilehash: 4989e8f5436b9da842e7a72173a73aced8591c25
ms.sourcegitcommit: 66f31cc4ce1236e638ab58d2f70d3646206386fa
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/27/2020
ms.locfileid: "85466918"
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

określoną Zwraca wartość `DWORD` , która zawiera unikatowy identyfikator jednostka kompilacji, który przyczynia się do tego wiersza.

## <a name="return-value"></a>Wartość zwracana
 Jeśli powiedzie się, zwraca `S_OK` . Zwraca wartość, `S_FALSE` Jeśli ta właściwość nie jest obsługiwana. W przeciwnym razie zwraca kod błędu.

## <a name="see-also"></a>Zobacz też
- [IDiaLineNumber](../../debugger/debug-interface-access/idialinenumber.md)