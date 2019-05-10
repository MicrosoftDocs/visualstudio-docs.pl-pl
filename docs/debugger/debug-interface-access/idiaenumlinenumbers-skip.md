---
title: Idiaenumlinenumbers::SKIP — | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumLineNumbers::Skip method
ms.assetid: d182c269-8c76-4d8b-8275-c6807c5ae4e1
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: e68eccfebfc5218d59649aa09162b20467ceb670
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62554017"
---
# <a name="idiaenumlinenumbersskip"></a>IDiaEnumLineNumbers::Skip
Pomija określoną liczbę numery wierszy w kolejności wyliczenia.

## <a name="syntax"></a>Składnia

```C++
HRESULT Skip ( 
   ULONG celt
);
```

#### <a name="parameters"></a>Parametry
 celt

[in] Liczba numerów wierszy w kolejności wyliczenia do pominięcia.

## <a name="return-value"></a>Wartość zwracana
 Jeśli operacja się powiedzie, zwraca `S_OK`; w przeciwnym razie zwraca `S_FALSE` przypadku bez więcej numerów wierszy do pominięcia.

## <a name="see-also"></a>Zobacz też
- [IDiaEnumLineNumbers](../../debugger/debug-interface-access/idiaenumlinenumbers.md)