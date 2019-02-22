---
title: IDiaSymbol::findChildrenExByVA | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::findChildrenExByVA
ms.assetid: 29080009-36e4-4697-acd7-50f2e3e1bf1b
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 85dc2d62134d57faf40162ff61b193b80b045e29
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/21/2019
ms.locfileid: "56613622"
---
# <a name="idiasymbolfindchildrenexbyva"></a>IDiaSymbol::findChildrenExByVA
Pobiera elementy podrzędne symbolu, które są prawidłowe na określony adres wirtualny.

## <a name="syntax"></a>Składnia

```C++
HRESULT findChildrenExByVA ( 
   enum SymTagEnum   symtag,
   LPCOLESTR         name,
   DWORD             compareFlags,
   DWORD             address,
   IDiaEnumSymbols** ppResult
);
```

#### <a name="parameters"></a>Parametry
 `symtag`

[in] Określa tagi symboli elementów podrzędnych, które mają zostać pobrane, zgodnie z definicją w [symtagenum — wyliczenie](../../debugger/debug-interface-access/symtagenum.md). Ustaw `SymTagNull` dla wszystkich elementów podrzędnych do pobrania.

 `name`

[in] Określa nazwę elementy podrzędne, które mają zostać pobrane. Ustaw `NULL` dla wszystkich elementów podrzędnych do pobrania.

 `compareFlags`

[in] Określa opcje porównywania, która ma zostać zastosowany do dopasowania nazwy. Wartości z kolekcji [namesearchoptions — wyliczenie](../../debugger/debug-interface-access/namesearchoptions.md) wyliczenia można samodzielnie lub w połączeniu.

 `address`

[in] Określa adres wirtualny.

 `ppResult`

[out] Zwraca [idiaenumsymbols —](../../debugger/debug-interface-access/idiaenumsymbols.md) pobrać obiekt, który zawiera listę symbolami podrzędnymi.

## <a name="return-value"></a>Wartość zwracana
 Zwraca `S_OK` Jeśli co najmniej jeden element podrzędny symbol został znaleziony lub zwraca `S_FALSE` Jeśli żadne elementy podrzędne nie znaleziono; w przeciwnym razie zwraca kod błędu.

## <a name="remarks"></a>Uwagi
 Symbole lokalne, które są zwracane zawierają informacje na żywo zakresu.

## <a name="requirements"></a>Wymagania
 Nagłówek: Dia2.h

 Biblioteka: diaguids.lib

 DLL: msdia100.dll

## <a name="see-also"></a>Zobacz też
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
- [SymTagEnum, wyliczenie](../../debugger/debug-interface-access/symtagenum.md)
- [IDiaEnumSymbols](../../debugger/debug-interface-access/idiaenumsymbols.md)
- [IDiaSession::findChildren](../../debugger/debug-interface-access/idiasession-findchildren.md)
- [NameSearchOptions, wyliczenie](../../debugger/debug-interface-access/namesearchoptions.md)