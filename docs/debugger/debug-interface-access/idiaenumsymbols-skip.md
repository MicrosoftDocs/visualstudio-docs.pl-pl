---
title: 'IDiaEnumSymbols:: Skip | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumSymbols::Skip method
ms.assetid: e601fbc9-b10b-41c7-8180-959e57efabe8
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: fea037e4e99cc5c8822987c30a94adf37ebe276e
ms.sourcegitcommit: 66f31cc4ce1236e638ab58d2f70d3646206386fa
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/27/2020
ms.locfileid: "85467709"
---
# <a name="idiaenumsymbolsskip"></a>IDiaEnumSymbols::Skip
Pomija określoną liczbę symboli w sekwencji wyliczenia.

## <a name="syntax"></a>Składnia

```C++
HRESULT Skip ( 
   ULONG celt
);
```

#### <a name="parameters"></a>Parametry
 celt

podczas Liczba symboli w sekwencji wyliczenia do pominięcia.

## <a name="return-value"></a>Wartość zwracana
 Jeśli powiedzie się, zwraca `S_OK` ; w przeciwnym razie zwraca `S_FALSE` czy nie ma więcej symboli do pominięcia.

## <a name="see-also"></a>Zobacz też
- [IDiaEnumSymbols](../../debugger/debug-interface-access/idiaenumsymbols.md)