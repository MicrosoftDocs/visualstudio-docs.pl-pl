---
title: 'IDiaSession:: findInlineeLinesByLinenum | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: cf32ae7c-a0c8-4800-bc8f-d64fdd15fb06
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: fe238f3bc66d6a7c5978c5d7cbebcd185fcd43d2
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/22/2019
ms.locfileid: "72742216"
---
# <a name="idiasessionfindinlineelinesbylinenum"></a>IDiaSession::findInlineeLinesByLinenum
Pobiera wyliczenie, które umożliwia klientowi przechodzenie do kolejnych informacji o numerze wiersza wszystkich funkcji, które są wbudowane, bezpośrednio lub pośrednio, w określonym pliku źródłowym i numerze wiersza.

## <a name="syntax"></a>Składnia

```C++
HRESULT findInlineeLinesByVA ( 
   IDiaSymbol*           compiland,
   IDiaSourceFile*       file,
   DWORD                 linenum,
   DWORD                 column,
   IDiaEnumLineNumbers** ppResult
);
```

#### <a name="parameters"></a>Parametry
 `compiland`

podczas Obiekt [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md) , który reprezentuje jednostka kompilacji do wyszukiwania numerów wierszy. Ten parametr nie może być `NULL`.

 `file`

podczas Obiekt [IDiaSourceFile](../../debugger/debug-interface-access/idiasourcefile.md) , który reprezentuje plik źródłowy, który ma zostać wyszukany. Ten parametr nie może być `NULL`.

 `linenum`

podczas Określa pojedynczy numer wiersza.

> [!NOTE]
> Nie można użyć zera do określenia wszystkich wierszy (Użyj metody [IDiaSession:: findLines](../../debugger/debug-interface-access/idiasession-findlines.md) , aby znaleźć wszystkie wiersze).

 `column`

podczas Określa numer kolumny. Użyj wartości zero, aby określić wszystkie kolumny. Kolumna jest przesunięciem bajtów do wiersza.

 `ppResult`

określoną Zwraca obiekt [IDiaEnumLineNumbers](../../debugger/debug-interface-access/idiaenumlinenumbers.md) , który zawiera listę numerów wierszy, które zostały pobrane.

## <a name="return-value"></a>Wartość zwracana
 Jeśli powiedzie się, zwraca `S_OK`; w przeciwnym razie zwraca kod błędu.

## <a name="see-also"></a>Zobacz także
- [IDiaSession](../../debugger/debug-interface-access/idiasession.md)
- [IDiaSourceFile](../../debugger/debug-interface-access/idiasourcefile.md)
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
- [SymTagEnum, wyliczenie](../../debugger/debug-interface-access/symtagenum.md)
- [IDiaEnumLineNumbers](../../debugger/debug-interface-access/idiaenumlinenumbers.md)