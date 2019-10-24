---
title: 'IDiaEnumLineNumbers:: Clone | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumLineNumbers::Clone method
ms.assetid: fcd2479a-8ff7-4aba-a737-06123c280d54
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 42e17066df5ece7efda46f2a389b5ae5756949ea
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/22/2019
ms.locfileid: "72744441"
---
# <a name="idiaenumlinenumbersclone"></a>IDiaEnumLineNumbers::Clone
Tworzy moduł wyliczający, który zawiera ten sam stan wyliczania co bieżący moduł wyliczający.

## <a name="syntax"></a>Składnia

```C++
HRESULT Clone ( 
   IDiaEnumLineNumbers** ppenum
);
```

#### <a name="parameters"></a>Parametry
 `ppenum`

określoną Zwraca obiekt [IDiaEnumLineNumbers](../../debugger/debug-interface-access/idiaenumlinenumbers.md) , który zawiera duplikat modułu wyliczającego. Numery wierszy nie są zduplikowane, tylko moduł wyliczający..

## <a name="return-value"></a>Wartość zwracana
 Jeśli powiedzie się, zwraca `S_OK`; w przeciwnym razie zwraca kod błędu.

## <a name="see-also"></a>Zobacz także
- [IDiaEnumLineNumbers](../../debugger/debug-interface-access/idiaenumlinenumbers.md)