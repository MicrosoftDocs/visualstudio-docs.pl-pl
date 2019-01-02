---
title: Idiaenumsymbols::SKIP — | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumSymbols::Skip method
ms.assetid: e601fbc9-b10b-41c7-8180-959e57efabe8
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 492748dc54f68d4f888b8cfb6ad8e27ec44435d0
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/02/2019
ms.locfileid: "53918628"
---
# <a name="idiaenumsymbolsskip"></a>IDiaEnumSymbols::Skip
Pomija określoną liczbę symboli w kolejności wyliczenia.  
  
## <a name="syntax"></a>Składnia  
  
```C++  
HRESULT Skip (   
   ULONG celt  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 celt  
 [in] Liczba symboli w kolejności wyliczenie, aby pominąć.  
  
## <a name="return-value"></a>Wartość zwracana  
 Jeśli operacja się powiedzie, zwraca `S_OK`; w przeciwnym razie zwraca `S_FALSE` przypadku żadnych więcej symboli, aby pominąć.  
  
## <a name="see-also"></a>Zobacz też  
 [IDiaEnumSymbols](../../debugger/debug-interface-access/idiaenumsymbols.md)