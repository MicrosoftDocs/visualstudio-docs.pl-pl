---
title: IDiaSession::findInlineesByName | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: 9860336d-f703-4ecb-bfc4-3f5beb175a76
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 1cb665e3c0965a2e85c8d28202114c95928988d5
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62839306"
---
# <a name="idiasessionfindinlineesbyname"></a>IDiaSession::findInlineesByName
Pobiera wyliczenie, które umożliwia klientowi do iterowania po informacje o numerze wiersza wszystkich funkcji śródwierszowych, które odpowiadają określonej nazwie.

## <a name="syntax"></a>Składnia

```C++
HRESULT findInlineesByName ( 
   LPCOLESTR             name,
   DWORD                 option,
   IDiaEnumLineNumbers** ppResult
);
```

#### <a name="parameters"></a>Parametry
 `name`

[in] Określa nazwę do użycia dla porównania.

 `option`

[in] Określa opcje porównywania stosowane do wyszukiwania nazwy. Wartości z kolekcji [namesearchoptions — wyliczenie](../../debugger/debug-interface-access/namesearchoptions.md) wyliczenia można samodzielnie lub w połączeniu.

 `ppResult`

[out] Zwraca [idiaenumlinenumbers —](../../debugger/debug-interface-access/idiaenumlinenumbers.md) obiektu, który zawiera listę numerów wierszy, które zostały pobrane.

## <a name="return-value"></a>Wartość zwracana
 Jeśli operacja się powiedzie, zwraca `S_OK`; w przeciwnym razie zwraca kod błędu.

## <a name="see-also"></a>Zobacz też
- [IDiaSession](../../debugger/debug-interface-access/idiasession.md)
- [IDiaSourceFile](../../debugger/debug-interface-access/idiasourcefile.md)
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
- [SymTagEnum, wyliczenie](../../debugger/debug-interface-access/symtagenum.md)
- [IDiaEnumLineNumbers](../../debugger/debug-interface-access/idiaenumlinenumbers.md)