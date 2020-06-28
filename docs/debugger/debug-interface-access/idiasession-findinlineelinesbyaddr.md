---
title: 'IDiaSession:: findInlineeLinesByAddr | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
ms.assetid: bb70e408-eed1-4c9c-b5b1-44323125f48b
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 4de373985230524dfe12703545a4690090ffce8e
ms.sourcegitcommit: 66f31cc4ce1236e638ab58d2f70d3646206386fa
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/27/2020
ms.locfileid: "85465805"
---
# <a name="idiasessionfindinlineelinesbyaddr"></a>IDiaSession::findInlineeLinesByAddr
Pobiera wyliczenie, które umożliwia klientowi przechodzenie do kolejnych informacji o numerze wiersza wszystkich funkcji, które są wbudowane, bezpośrednio lub pośrednio, przez określony symbol nadrzędny i są zawarte w określonym zakresie adresów.

## <a name="syntax"></a>Składnia

```C++
HRESULT findInlineeLinesByAddr ( 
   IDiaSymbol*           parent,   DWORD                 isect,   DWORD                 offset,   DWORD                 length,
   IDiaEnumLineNumbers** ppResult
);
```

#### <a name="parameters"></a>Parametry
 `parent`

podczas `IDiaSymbol`Obiekt reprezentujący element nadrzędny.

 `isect`

podczas Określa składnik sekcji adresu.

 `offset`

podczas Określa składnik przesunięcia adresu.

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