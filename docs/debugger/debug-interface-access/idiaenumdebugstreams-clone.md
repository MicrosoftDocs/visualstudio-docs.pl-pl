---
description: Tworzy moduł wyliczający, który zawiera ten sam stan wyliczania co bieżący moduł wyliczający strumienia debugowania.
title: 'IDiaEnumDebugStreams:: Clone | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumDebugStreams::Clone method
ms.assetid: e85ec592-de97-4f95-a774-1623315ba415
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 21b026bd717d20777da1eaa5b815039164abc6b9
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/05/2021
ms.locfileid: "102158163"
---
# <a name="idiaenumdebugstreamsclone"></a>IDiaEnumDebugStreams::Clone
Tworzy moduł wyliczający, który zawiera ten sam stan wyliczania co bieżący moduł wyliczający.

## <a name="syntax"></a>Składnia

```C++
HRESULT Clone ( 
   IDiaEnumDebugStreams** ppenum
);
```

#### <a name="parameters"></a>Parametry
 `ppenum`

określoną Zwraca obiekt [IDiaEnumDebugStreams](../../debugger/debug-interface-access/idiaenumdebugstreams.md) , który zawiera duplikat modułu wyliczającego. Strumienie nie są duplikowane, tylko moduł wyliczający.

## <a name="return-value"></a>Wartość zwracana
 Jeśli powiedzie się, zwraca `S_OK` ; w przeciwnym razie zwraca kod błędu.

## <a name="see-also"></a>Zobacz też
- [IDiaEnumDebugStreams](../../debugger/debug-interface-access/idiaenumdebugstreams.md)
