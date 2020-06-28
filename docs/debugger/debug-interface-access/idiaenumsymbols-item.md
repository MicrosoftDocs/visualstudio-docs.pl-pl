---
title: 'IDiaEnumSymbols:: Item | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumSymbols::Item method
ms.assetid: 2bd1ec04-e677-4e32-8e32-33334f1eed77
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 58e00d55a26f3aaf771eed01135c62b607794876
ms.sourcegitcommit: 66f31cc4ce1236e638ab58d2f70d3646206386fa
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/27/2020
ms.locfileid: "85467758"
---
# <a name="idiaenumsymbolsitem"></a>IDiaEnumSymbols::Item
Pobiera symbol przy użyciu indeksu.

## <a name="syntax"></a>Składnia

```C++
HRESULT Item ( 
   DWORD        index,
   IDiaSymbol** symbol
);
```

#### <a name="parameters"></a>Parametry
 indeks

podczas Indeks obiektu [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md) do pobrania. Indeks znajduje się w zakresie od 0 do `count` -1, gdzie `count` jest zwracany przez metodę [IDiaEnumSymbols:: get_Count](../../debugger/debug-interface-access/idiaenumsymbols-get-count.md) .

  — symbol

określoną Zwraca obiekt [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md) reprezentujący żądany symbol.

## <a name="return-value"></a>Wartość zwracana
 Jeśli powiedzie się, zwraca `S_OK` ; w przeciwnym razie zwraca kod błędu.

## <a name="see-also"></a>Zobacz też
- [IDiaEnumSymbols](../../debugger/debug-interface-access/idiaenumsymbols.md)
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)