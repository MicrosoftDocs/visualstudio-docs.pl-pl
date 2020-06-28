---
title: 'IDiaEnumStackFrames:: Next | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumStackFrames::Next method
ms.assetid: 09378a21-d5e3-4213-b7e2-10f04d85295f
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 77d50a6c59ea376950d8cd4653f29ba7d04f36ad
ms.sourcegitcommit: 66f31cc4ce1236e638ab58d2f70d3646206386fa
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/27/2020
ms.locfileid: "85467842"
---
# <a name="idiaenumstackframesnext"></a>IDiaEnumStackFrames::Next
Pobiera określoną liczbę elementów ramek stosu z sekwencji wyliczenia.

## <a name="syntax"></a>Składnia

```C++
HRESULT Next( 
   ULONG             celt,
   IDiaStackFrame**  rgelt,
   ULONG*            pceltFetched
);
```

#### <a name="parameters"></a>Parametry
 celt

podczas Liczba elementów StackFrame w module wyliczającym do pobrania.

 rgelt

określoną Tablica, która ma zostać wypełniona z żądanymi obiektami [IDiaStackFrame](../../debugger/debug-interface-access/idiastackframe.md) .

 pceltFetched

określoną Zwraca liczbę elementów ramek stosu w ramach pobranego modułu wyliczającego.

## <a name="return-value"></a>Wartość zwracana
 Jeśli powiedzie się, zwraca `S_OK` . Zwraca `S_FALSE` czy nie ma więcej ramek stosu. W przeciwnym razie zwraca kod błędu.

## <a name="see-also"></a>Zobacz też
- [IDiaEnumStackFrames](../../debugger/debug-interface-access/idiaenumstackframes.md)
- [IDiaStackFrame](../../debugger/debug-interface-access/idiastackframe.md)