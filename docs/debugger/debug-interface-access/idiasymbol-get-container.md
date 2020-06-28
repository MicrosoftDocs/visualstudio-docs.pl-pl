---
title: 'IDiaSymbol:: get_container | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_container method
ms.assetid: 24e832eb-80b3-484c-a41b-11477ec9de99
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 62bb2f29d737aeb09cc228038be96480922e204c
ms.sourcegitcommit: 66f31cc4ce1236e638ab58d2f70d3646206386fa
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/27/2020
ms.locfileid: "85464031"
---
# <a name="idiasymbolget_container"></a>IDiaSymbol::get_container
Ta funkcja Pobiera wskaźnik do symbolu reprezentującego element nadrzędny/kontener tego symbolu.

## <a name="syntax"></a>Składnia

```C++
HRESULT get_container(
   IDiaSymbol **pRetVal
);
```

#### <a name="parameters"></a>Parametry
 `pRetVal`

określoną Zwraca wskaźnik do `IDiaSymbol` zawierającego je informacji o kontenerze tego symbolu.

## <a name="return-value"></a>Wartość zwracana
 Jeśli powiedzie się, zwraca S_OK; w przeciwnym razie zwraca S_FALSE lub kod błędu.

> [!NOTE]
> Wartość zwracana przez S_FALSE oznacza, że właściwość nie jest dostępna dla symbolu.

## <a name="requirements"></a>Wymagania

|Wymaganie|Opis|
|-----------------|-----------------|
|Nagłówki|dia2. h|
|Wersja:|DIA SDK v 8.0|

## <a name="see-also"></a>Zobacz też
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)