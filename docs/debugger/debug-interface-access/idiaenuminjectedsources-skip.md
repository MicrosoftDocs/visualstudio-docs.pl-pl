---
title: 'IDiaEnumInjectedSources:: Skip | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumInjectedSources::Skip method
ms.assetid: 4aad6a51-f2d3-4064-b216-60d830d0a560
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: b8cfac0306d95dffb2b6879e9bdc930719eb77ac
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "85468253"
---
# <a name="idiaenuminjectedsourcesskip"></a>IDiaEnumInjectedSources::Skip
Pomija określoną liczbę wprowadzonych źródeł w sekwencji wyliczenia.

## <a name="syntax"></a>Składnia

```C++
HRESULT Skip ( 
   ULONG celt
);
```

#### <a name="parameters"></a>Parametry
 celt

podczas Liczba wstrzykniętych źródeł w sekwencji wyliczenia do pominięcia.

## <a name="return-value"></a>Wartość zwracana
 Jeśli powiedzie się, zwraca `S_OK` ; w przeciwnym razie zwraca `S_FALSE` czy nie ma więcej wstrzykiwanych źródeł do pominięcia.

## <a name="see-also"></a>Zobacz też
- [IDiaEnumInjectedSources](../../debugger/debug-interface-access/idiaenuminjectedsources.md)