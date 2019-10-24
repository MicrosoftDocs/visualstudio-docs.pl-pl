---
title: 'IDiaEnumInjectedSources:: Clone | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumInjectedSources::Clone method
ms.assetid: 18038691-c140-426a-8617-27f0360650f3
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 9baba1709e3e89a982c0347cb744950a14cbb0b8
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/22/2019
ms.locfileid: "72744541"
---
# <a name="idiaenuminjectedsourcesclone"></a>IDiaEnumInjectedSources::Clone
Tworzy moduł wyliczający, który zawiera ten sam stan wyliczania co bieżący moduł wyliczający.

## <a name="syntax"></a>Składnia

```C++
HRESULT Clone ( 
   IDiaEnumInjectedSources** ppenum
);
```

#### <a name="parameters"></a>Parametry
 `ppenum`

określoną Zwraca obiekt [IDiaEnumInjectedSources](../../debugger/debug-interface-access/idiaenuminjectedsources.md) , który zawiera duplikat modułu wyliczającego. Wprowadzone źródła nie są duplikowane, tylko moduł wyliczający.

## <a name="return-value"></a>Wartość zwracana
 Jeśli powiedzie się, zwraca `S_OK`; w przeciwnym razie zwraca kod błędu.

## <a name="see-also"></a>Zobacz także
- [IDiaEnumInjectedSources](../../debugger/debug-interface-access/idiaenuminjectedsources.md)