---
description: Pomija określoną liczbę udziałów sekcji w sekwencji wyliczenia.
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
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 345aa9219071a64fdd497a9e5409ee7dab3068ad
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/05/2021
ms.locfileid: "102159301"
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
