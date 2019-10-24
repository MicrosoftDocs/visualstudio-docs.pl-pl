---
title: 'IDiaInjectedSource:: get_sourceCompression | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaInjectedSource::get_sourceCompression method
ms.assetid: 854b142f-23a9-466c-bf7f-98e581d5abcd
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 9428b30df82d92a8c74511644aaf97f2166807a2
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/22/2019
ms.locfileid: "72743317"
---
# <a name="idiainjectedsourceget_sourcecompression"></a>IDiaInjectedSource::get_sourceCompression
Pobiera wskaźnik używanej kompresji źródłowej.

## <a name="syntax"></a>Składnia

```C++
HRESULT get_sourceCompression ( 
   DWORD* pRetVal
);
```

#### <a name="parameters"></a>Parametry
 `pRetVal`

określoną Zwraca wskaźnik używanej kompresji źródłowej. Wartość zerowa wskazuje, że nie użyto kompresji źródłowej.

## <a name="return-value"></a>Wartość zwracana
 Jeśli powiedzie się, zwraca `S_OK`. Zwraca `S_FALSE`, jeśli ta właściwość nie jest obsługiwana. W przeciwnym razie zwraca kod błędu.

## <a name="remarks"></a>Uwagi
 Wartość zwracana przez tę metodę jest specyficzna dla używanego kompilatora. Na przykład kompilator może użyć kodowania o długości uruchomienia lub kompresji w stylu Huffmana.

## <a name="see-also"></a>Zobacz także
- [IDiaInjectedSource](../../debugger/debug-interface-access/idiainjectedsource.md)