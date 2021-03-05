---
description: Pobiera unikatowy identyfikator jednostka kompilacji, który przyczynia się do tego wiersza.
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
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 090b8ac199ab709c453bd5f3280afe1abd088077
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/05/2021
ms.locfileid: "102157582"
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
