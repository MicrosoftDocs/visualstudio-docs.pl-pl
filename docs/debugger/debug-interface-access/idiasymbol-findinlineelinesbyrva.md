---
title: 'IDiaSymbol:: findInlineeLinesByRVA | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
ms.assetid: ac108db1-9dbf-4dc4-bf48-159ca8d3725c
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 26941012b28bb114771472452e158823d988faab
ms.sourcegitcommit: 66f31cc4ce1236e638ab58d2f70d3646206386fa
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/27/2020
ms.locfileid: "85464521"
---
# <a name="idiasymbolfindinlineelinesbyrva"></a>IDiaSymbol::findInlineeLinesByRVA
Pobiera wyliczenie, które umożliwia klientowi przechodzenie do kolejnych informacji o numerze wiersza wszystkich funkcji, które są wbudowane, bezpośrednio lub pośrednio, w tym symbolu w ramach określonego względnego adresu wirtualnego (RVA).

## <a name="syntax"></a>Składnia

```C++
HRESULT findInlineeLinesByRVA (    DWORD                 rva,   DWORD                 length,
   IDiaEnumLineNumbers** ppResult
);
```

#### <a name="parameters"></a>Parametry
 `rva`

podczas Określa adres jako RVA.

 `length`

podczas Określa zakres adresów (w bajtach), który będzie obejmować to zapytanie.

 `ppResult`

określoną Zawiera `IDiaEnumLineNumbers` obiekt zawierający listę numerów wierszy, które są pobierane.

## <a name="return-value"></a>Wartość zwracana
 Jeśli powiedzie się, zwraca `S_OK` ; w przeciwnym razie zwraca kod błędu.

## <a name="see-also"></a>Zobacz też
- [IDiaSession](../../debugger/debug-interface-access/idiasession.md)
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
- [SymTagEnum, wyliczenie](../../debugger/debug-interface-access/symtagenum.md)
- [IDiaEnumLineNumbers](../../debugger/debug-interface-access/idiaenumlinenumbers.md)
- [IDiaSession::findInlineeLines](../../debugger/debug-interface-access/idiasession-findinlineelines.md)