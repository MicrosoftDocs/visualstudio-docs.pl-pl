---
title: Idiatable::Item — | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaTable::Item method
ms.assetid: eae11b26-4807-400c-be25-e85bbc0c6b20
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 3e8ba825c0dba1b0218e53f9ad66f6958602d0c2
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/02/2019
ms.locfileid: "53953982"
---
# <a name="idiatableitem"></a>IDiaTable::Item
Pobiera odwołanie do określonego wpisu w tabeli.  
  
## <a name="syntax"></a>Składnia  
  
```C++  
HRESULT Item (   
   DWORD      index,  
   IUnknown** element  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `index`  
 [in] Indeks wpisu tabeli z zakresu od 0 do `count`-1, gdzie `count` jest zwracany przez [idiatable::get_count —](../../debugger/debug-interface-access/idiatable-get-count.md)metody.  
  
 `element`  
 [out] Zwraca `IUnknown` obiekt, który reprezentuje wpis określonej tabeli.  
  
## <a name="return-value"></a>Wartość zwracana  
 Jeśli operacja się powiedzie, zwraca `S_OK`; w przeciwnym razie zwraca kod błędu.  
  
## <a name="remarks"></a>Uwagi  
 Tabela reprezentuje kolekcję obiektów. W zależności od tych obiektów parametru elementu mogą być rzutowane na odpowiedni interfejs. Na przykład, jeśli tabela zawiera [idiasegment —](../../debugger/debug-interface-access/idiasegment.md) obiektów, a następnie można rzutować parametru elementu `IDiaSegment` interfejsu.  
  
 Jest bardziej powszechne podejście do wywołania `QueryInterface` method in Class metoda [idiatable —](../../debugger/debug-interface-access/idiatable.md) interfejsu dla interfejsu odpowiedniego modułu wyliczającego i umożliwia dostęp do treści modułu wyliczającego konkretnych metod. Zobacz [idiaenuminjectedsources —](../../debugger/debug-interface-access/idiaenuminjectedsources.md) interfejsu, na przykład.  
  
## <a name="see-also"></a>Zobacz też  
 [Idiatable —](../../debugger/debug-interface-access/idiatable.md)   
 [Idiatable::get_count —](../../debugger/debug-interface-access/idiatable-get-count.md)   
 [Idiasegment —](../../debugger/debug-interface-access/idiasegment.md)   
 [IDiaEnumInjectedSources](../../debugger/debug-interface-access/idiaenuminjectedsources.md)