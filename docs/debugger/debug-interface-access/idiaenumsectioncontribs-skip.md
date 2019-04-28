---
title: Idiaenumsectioncontribs::SKIP — | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
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
ms.openlocfilehash: c90c2148fc5a563fef8946bd39acf4603d7d09f6
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62833236"
---
# <a name="idiaenumsectioncontribsskip"></a>IDiaEnumSectionContribs::Skip
Pomija określoną liczbę sekcji wkład w kolejności wyliczenia.

## <a name="syntax"></a>Składnia

```C++
HRESULT Skip( 
   ULONG celt
);
```

#### <a name="parameters"></a>Parametry
 `celt`

[in] Liczba sekcji wkład w kolejności wyliczenie, aby pominąć.

## <a name="return-value"></a>Wartość zwracana
 Jeśli operacja się powiedzie, zwraca `S_OK`; w przeciwnym razie zwraca `S_FALSE` Jeśli nie ma żadnych więcej wkładów sekcji, aby pominąć.

## <a name="see-also"></a>Zobacz też
- [IDiaEnumSectionContribs](../../debugger/debug-interface-access/idiaenumsectioncontribs.md)