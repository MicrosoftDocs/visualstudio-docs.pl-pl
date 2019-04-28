---
title: IDiaTable::Item | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaTable::Item method
ms.assetid: eae11b26-4807-400c-be25-e85bbc0c6b20
caps.latest.revision: 12
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 6112a4580a68a98407723afab1ec3310d0f1cca9
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62574804"
---
# <a name="idiatableitem"></a>IDiaTable::Item
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Pobiera odwołanie do określonego wpisu w tabeli.  
  
## <a name="syntax"></a>Składnia  
  
```cpp#  
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
 [IDiaTable::get_Count](../../debugger/debug-interface-access/idiatable-get-count.md)   
 [Idiasegment —](../../debugger/debug-interface-access/idiasegment.md)   
 [IDiaEnumInjectedSources](../../debugger/debug-interface-access/idiaenuminjectedsources.md)
