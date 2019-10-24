---
title: 'IDiaSession:: findInlineeLinesByVA | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: dffe6594-e0d1-4ed5-aeea-8773f88d82a6
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 24807114cbb28c4112f538b8aa88b26bf5491fef
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/22/2019
ms.locfileid: "72742195"
---
# <a name="idiasessionfindinlineelinesbyva"></a>IDiaSession::findInlineeLinesByVA
Pobiera wyliczenie, które umożliwia klientowi przechodzenie do kolejnych informacji o numerze wiersza wszystkich funkcji, które są wbudowane, bezpośrednio lub pośrednio, przez określony symbol nadrzędny i są zawarte w określonym adresie wirtualnym (VA).

## <a name="syntax"></a>Składnia

```C++
HRESULT findInlineeLinesByVA ( 
   IDiaSymbol*           parent,   ULONGLONG             va,   DWORD                 length,
   IDiaEnumLineNumbers** ppResult
);
```

#### <a name="parameters"></a>Parametry
 `parent`

podczas Obiekt `IDiaSymbol` reprezentujący element nadrzędny.

 `va`

podczas Określa adres jako VA.

 `length`

podczas Określa zakres adresów (w bajtach), który będzie obejmować to zapytanie.

 `ppResult`

określoną Zawiera obiekt `IDiaEnumLineNumbers` zawierający listę numerów wierszy, które są pobierane.

## <a name="return-value"></a>Wartość zwracana
 Jeśli powiedzie się, zwraca `S_OK`; w przeciwnym razie zwraca kod błędu.

## <a name="see-also"></a>Zobacz także
- [IDiaSession](../../debugger/debug-interface-access/idiasession.md)
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
- [SymTagEnum, wyliczenie](../../debugger/debug-interface-access/symtagenum.md)
- [IDiaEnumLineNumbers](../../debugger/debug-interface-access/idiaenumlinenumbers.md)