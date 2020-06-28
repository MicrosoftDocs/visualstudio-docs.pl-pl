---
title: 'IDiaEnumSectionContribs:: Item | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
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
ms.openlocfilehash: 2f66d2ca43cba50d40bc7c8fc09b85bf252d352f
ms.sourcegitcommit: 66f31cc4ce1236e638ab58d2f70d3646206386fa
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/27/2020
ms.locfileid: "85468149"
---
# <a name="idiaenumsectioncontribsitem"></a>IDiaEnumSectionContribs::Item
Pobiera udziały sekcji za pomocą indeksu.

## <a name="syntax"></a>Składnia

```C++
HRESULT Item ( 
   DWORD                index,
   IDiaSectionContrib** section
);
```

#### <a name="parameters"></a>Parametry
 indeks

podczas Indeks obiektu [IDiaSectionContrib](../../debugger/debug-interface-access/idiasectioncontrib.md) do pobrania. Indeks znajduje się w zakresie od 0 do `count` -1, gdzie `count` jest zwracany przez metodę [IDiaEnumSectionContribs:: get_Count](../../debugger/debug-interface-access/idiaenumsectioncontribs-get-count.md) .

 section

określoną Zwraca obiekt [IDiaSectionContrib](../../debugger/debug-interface-access/idiasectioncontrib.md) reprezentujący żądany udział sekcji.

## <a name="return-value"></a>Wartość zwracana
 Jeśli powiedzie się, zwraca `S_OK` ; w przeciwnym razie zwraca kod błędu.

## <a name="see-also"></a>Zobacz też
- [IDiaEnumSectionContribs::get_Count](../../debugger/debug-interface-access/idiaenumsectioncontribs-get-count.md)
- [IDiaSectionContrib](../../debugger/debug-interface-access/idiasectioncontrib.md)