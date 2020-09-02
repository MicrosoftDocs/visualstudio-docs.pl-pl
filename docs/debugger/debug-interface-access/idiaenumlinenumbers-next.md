---
title: 'IDiaEnumLineNumbers:: Next | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumLineNumbers::Next method
ms.assetid: 363d5b40-1316-4ab8-836f-63637f619e0a
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 1546c0bc7b8682b918d583769a9f580323c9dda4
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "85468211"
---
# <a name="idiaenumlinenumbersnext"></a>IDiaEnumLineNumbers::Next
Pobiera określoną liczbę numerów wierszy w sekwencji wyliczenia.

## <a name="syntax"></a>Składnia

```C++
HRESULT Next ( 
   ULONG            celt,
   IDiaLineNumber** rgelt,
   ULONG*           pceltFetched
);
```

#### <a name="parameters"></a>Parametry
 celt

podczas Liczba numerów wierszy w module wyliczającym do pobrania.

 rgelt

określoną Zwraca tablicę obiektów [IDiaLineNumber](../../debugger/debug-interface-access/idialinenumber.md) reprezentujących żądane numery wierszy.

 pceltFetched

określoną Zwraca liczbę wierszy w ramach pobranego modułu wyliczającego.

## <a name="return-value"></a>Wartość zwracana
 Jeśli powiedzie się, zwraca `S_OK` . Zwraca `S_FALSE` czy nie ma więcej numerów wierszy. W przeciwnym razie zwraca kod błędu.

## <a name="see-also"></a>Zobacz też
- [IDiaEnumLineNumbers](../../debugger/debug-interface-access/idiaenumlinenumbers.md)
- [IDiaLineNumber](../../debugger/debug-interface-access/idialinenumber.md)
- [IDiaSession::findLinesByLinenum](../../debugger/debug-interface-access/idiasession-findlinesbylinenum.md)