---
title: 'IDiaTable:: Item | Microsoft Docs'
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
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
 podczas Indeks wpisu tabeli w zakresie od 0 do `count` -1, gdzie `count` jest zwracany przez metodę [IDiaTable:: get_Count](../../debugger/debug-interface-access/idiatable-get-count.md).  
  
 `element`  
 określoną Zwraca `IUnknown` obiekt, który reprezentuje określony wpis w tabeli.  
  
## <a name="return-value"></a>Wartość zwracana  
 Jeśli powiedzie się, zwraca `S_OK` ; w przeciwnym razie zwraca kod błędu.  
  
## <a name="remarks"></a>Uwagi  
 Tabela reprezentuje kolekcję obiektów. W zależności od tych obiektów parametr elementu może być rzutowany do odpowiedniego interfejsu. Na przykład jeśli tabela zawiera obiekty [IDiaSegment](../../debugger/debug-interface-access/idiasegment.md) , parametr elementu może być rzutowany do `IDiaSegment` interfejsu.  
  
 Jest to bardziej typowe podejście do wywołania `QueryInterface` metody w interfejsie [IDiaTable](../../debugger/debug-interface-access/idiatable.md) dla odpowiedniego interfejsu modułu wyliczającego i używania określonych metod modułu wyliczającego w celu uzyskania dostępu do zawartości tabeli. Zapoznaj się z przykładowym interfejsem [IDiaEnumInjectedSources](../../debugger/debug-interface-access/idiaenuminjectedsources.md) .  
  
## <a name="see-also"></a>Zobacz też  
 [IDiaTable](../../debugger/debug-interface-access/idiatable.md)   
 [IDiaTable:: get_Count](../../debugger/debug-interface-access/idiatable-get-count.md)   
 [IDiaSegment](../../debugger/debug-interface-access/idiasegment.md)   
 [IDiaEnumInjectedSources](../../debugger/debug-interface-access/idiaenuminjectedsources.md)
