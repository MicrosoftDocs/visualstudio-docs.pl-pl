---
title: Idiaenumsectioncontribs::Item — | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumSectionContribs::Item method
ms.assetid: 63a28f23-0ca0-44a7-b11b-ca0206d642a0
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 3e14092c21497cc0126eb3eed169286418527c54
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/26/2019
ms.locfileid: "55069372"
---
# <a name="idiaenumsectioncontribsitem"></a>IDiaEnumSectionContribs::Item
Pobiera sekcji wkładów za pomocą indeksu.  
  
## <a name="syntax"></a>Składnia  
  
```C++  
HRESULT Item (   
   DWORD                index,  
   IDiaSectionContrib** section  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 indeks  
 [in] Indeks elementu [idiasectioncontrib —](../../debugger/debug-interface-access/idiasectioncontrib.md) obiektu do pobrania. Indeks znajduje się w zakresie od 0 do `count`-1, gdzie `count` jest zwracany przez [idiaenumsectioncontribs::get_count —](../../debugger/debug-interface-access/idiaenumsectioncontribs-get-count.md) metody.  
  
 sekcja  
 [out] Zwraca [idiasectioncontrib —](../../debugger/debug-interface-access/idiasectioncontrib.md) obiekt reprezentujący wkład odpowiednią sekcję.  
  
## <a name="return-value"></a>Wartość zwracana  
 Jeśli operacja się powiedzie, zwraca `S_OK`; w przeciwnym razie zwraca kod błędu.  
  
## <a name="see-also"></a>Zobacz też  
 [IDiaEnumSectionContribs::get_Count](../../debugger/debug-interface-access/idiaenumsectioncontribs-get-count.md)   
 [IDiaSectionContrib](../../debugger/debug-interface-access/idiasectioncontrib.md)