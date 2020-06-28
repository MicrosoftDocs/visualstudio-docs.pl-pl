---
title: 'IDiaEnumSectionContribs:: Next | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumSectionContribs::Next method
ms.assetid: a6bb2adb-ee6d-4f3c-ab5b-e89361c8880e
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 09622b1b152a8d1efd105b9b18a3c1fa74835378
ms.sourcegitcommit: 66f31cc4ce1236e638ab58d2f70d3646206386fa
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/27/2020
ms.locfileid: "85468115"
---
# <a name="idiaenumsectioncontribsnext"></a>IDiaEnumSectionContribs::Next
Pobiera określoną liczbę udziałów sekcji w sekwencji wyliczenia.

## <a name="syntax"></a>Składnia

```C++
HRESULT Next( 
   ULONG                celt,
   IDiaSectionContrib** rgelt,
   ULONG*               pceltFetched
);
```

#### <a name="parameters"></a>Parametry
 celt

podczas Liczba udziałów sekcji w module wyliczającym do pobrania.

 rgelt

określoną Tablica, która ma zostać wypełniona obiektami [IDiaSectionContrib](../../debugger/debug-interface-access/idiasectioncontrib.md) , które reprezentują żądane wkłady sekcji.

 pceltFetched

określoną Zwraca liczbę udziałów sekcji w pobieranym module wyliczającym.

## <a name="return-value"></a>Wartość zwracana
 Jeśli powiedzie się, zwraca `S_OK` . Zwraca `S_FALSE` czy nie ma więcej udziałów w sekcji. W przeciwnym razie zwraca kod błędu.

## <a name="see-also"></a>Zobacz też
- [IDiaEnumSectionContribs](../../debugger/debug-interface-access/idiaenumsectioncontribs.md)
- [IDiaSectionContrib](../../debugger/debug-interface-access/idiasectioncontrib.md)