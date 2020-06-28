---
title: 'IDiaEnumSectionContribs:: Skip | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumSectionContribs::Skip method
ms.assetid: 7471a178-5134-41b2-80a6-51ff96abe916
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 0e13f9290c76eb558bea397f7921f7cfd765613f
ms.sourcegitcommit: 66f31cc4ce1236e638ab58d2f70d3646206386fa
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/27/2020
ms.locfileid: "85468094"
---
# <a name="idiaenumsectioncontribsskip"></a>IDiaEnumSectionContribs::Skip
Pomija określoną liczbę udziałów sekcji w sekwencji wyliczenia.

## <a name="syntax"></a>Składnia

```C++
HRESULT Skip( 
   ULONG celt
);
```

#### <a name="parameters"></a>Parametry
 `celt`

podczas Liczba udziałów sekcji w sekwencji wyliczenia do pominięcia.

## <a name="return-value"></a>Wartość zwracana
 Jeśli powiedzie się, zwraca `S_OK` ; w przeciwnym razie zwraca, `S_FALSE` czy nie ma więcej udziałów sekcji do pominięcia.

## <a name="see-also"></a>Zobacz też
- [IDiaEnumSectionContribs](../../debugger/debug-interface-access/idiaenumsectioncontribs.md)