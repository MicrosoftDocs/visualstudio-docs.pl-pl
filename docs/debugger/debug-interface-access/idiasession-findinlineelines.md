---
title: 'IDiaSession:: findInlineeLines | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: b6822d8b-70d5-470b-8278-3aec4680326c
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 5103a881b1b046479a1a3156f06038e230f5063e
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/22/2019
ms.locfileid: "72742240"
---
# <a name="idiasessionfindinlineelines"></a>IDiaSession::findInlineeLines
Pobiera wyliczenie, które umożliwia klientowi przechodzenie do kolejnych informacji o numerze wiersza wszystkich funkcji, które są wbudowane, bezpośrednio lub pośrednio, przez określony symbol nadrzędny.

## <a name="syntax"></a>Składnia

```C++
HRESULT findInlineeLines ( 
   IDiaSymbol*       parent,
   IDiaEnumLineNumbers** ppResult
);
```

#### <a name="parameters"></a>Parametry
 `parent`

podczas Obiekt `IDiaSymbol` reprezentujący element nadrzędny.

 `ppResult`

określoną Zawiera obiekt `IDiaEnumLineNumbers` zawierający listę numerów wierszy, które są pobierane.

## <a name="return-value"></a>Wartość zwracana
 Jeśli powiedzie się, zwraca `S_OK`; w przeciwnym razie zwraca kod błędu.

## <a name="see-also"></a>Zobacz także
- [IDiaSession](../../debugger/debug-interface-access/idiasession.md)
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
- [SymTagEnum, wyliczenie](../../debugger/debug-interface-access/symtagenum.md)
- [IDiaEnumLineNumbers](../../debugger/debug-interface-access/idiaenumlinenumbers.md)