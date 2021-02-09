---
title: 'IDiaTable:: Item | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaTable::Item method
ms.assetid: eae11b26-4807-400c-be25-e85bbc0c6b20
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: db3baeaf7c30e0fa381c1d99d7a53e1eac5e2862
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99853269"
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

podczas Indeks wpisu tabeli w zakresie od 0 do `count` -1, gdzie `count` jest zwracany przez metodę [IDiaTable:: get_Count](../../debugger/debug-interface-access/idiatable-get-count.md).

 `element`

określoną Zwraca `IUnknown` obiekt, który reprezentuje określony wpis w tabeli.

## <a name="return-value"></a>Wartość zwracana
 Jeśli powiedzie się, zwraca `S_OK` ; w przeciwnym razie zwraca kod błędu.

## <a name="remarks"></a>Uwagi
 Tabela reprezentuje kolekcję obiektów. W zależności od tych obiektów parametr elementu może być rzutowany do odpowiedniego interfejsu. Na przykład jeśli tabela zawiera obiekty [IDiaSegment](../../debugger/debug-interface-access/idiasegment.md) , parametr elementu może być rzutowany do `IDiaSegment` interfejsu.

 Jest to bardziej typowe podejście do wywołania `QueryInterface` metody w interfejsie [IDiaTable](../../debugger/debug-interface-access/idiatable.md) dla odpowiedniego interfejsu modułu wyliczającego i używania określonych metod modułu wyliczającego w celu uzyskania dostępu do zawartości tabeli. Zapoznaj się z przykładowym interfejsem [IDiaEnumInjectedSources](../../debugger/debug-interface-access/idiaenuminjectedsources.md) .

## <a name="see-also"></a>Zobacz też
- [IDiaTable](../../debugger/debug-interface-access/idiatable.md)
- [IDiaTable::get_Count](../../debugger/debug-interface-access/idiatable-get-count.md)
- [IDiaSegment](../../debugger/debug-interface-access/idiasegment.md)
- [IDiaEnumInjectedSources](../../debugger/debug-interface-access/idiaenuminjectedsources.md)