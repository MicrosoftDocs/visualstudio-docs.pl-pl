---
title: IDiaSession::findInlineeLinesByVA | Dokumentacja firmy Microsoft
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
ms.openlocfilehash: 58f572fcce0b490fad8f94f1e3e3d941e8568211
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62827722"
---
# <a name="idiasessionfindinlineelinesbyva"></a>IDiaSession::findInlineeLinesByVA
Pobiera wyliczenie, które umożliwia klientowi iteracyjne przeglądanie informacji o numerze wiersza wszystkich funkcji, które są śródwierszowych, bezpośrednio lub pośrednio, za pomocą symbolu określonego elementu nadrzędnego i znajdują się w określonym wirtualnego adresu (oceny luk w zabezpieczeniach).

## <a name="syntax"></a>Składnia

```C++
HRESULT findInlineeLinesByVA ( 
   IDiaSymbol*           parent,   ULONGLONG             va,   DWORD                 length,
   IDiaEnumLineNumbers** ppResult
);
```

#### <a name="parameters"></a>Parametry
 `parent`

[in] `IDiaSymbol` Obiekt reprezentujący element nadrzędny.

 `va`

[in] Określa adres jako VA.

 `length`

[in] Określa zakres adresów w liczbę bajtów, aby pokrywał się z tym zapytaniem.

 `ppResult`

[out] Przechowuje `IDiaEnumLineNumbers` obiektu, który zawiera listę numerów wierszy, które są pobierane.

## <a name="return-value"></a>Wartość zwracana
 Jeśli operacja się powiedzie, zwraca `S_OK`; w przeciwnym razie zwraca kod błędu.

## <a name="see-also"></a>Zobacz też
- [IDiaSession](../../debugger/debug-interface-access/idiasession.md)
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
- [SymTagEnum, wyliczenie](../../debugger/debug-interface-access/symtagenum.md)
- [IDiaEnumLineNumbers](../../debugger/debug-interface-access/idiaenumlinenumbers.md)