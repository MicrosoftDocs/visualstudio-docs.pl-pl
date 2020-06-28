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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 18efd1113d66d36b99dd33eb3e79cb0cc7e8bb05
ms.sourcegitcommit: 66f31cc4ce1236e638ab58d2f70d3646206386fa
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/27/2020
ms.locfileid: "85461302"
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