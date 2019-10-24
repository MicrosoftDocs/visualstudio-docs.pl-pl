---
title: 'IDiaSymbol:: findChildrenExByVA | Microsoft Docs'
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
ms.openlocfilehash: d9cc9f540b200ff6fdf4736b6a0bf64175a5ee3e
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/22/2019
ms.locfileid: "72741243"
---
# <a name="idiasymbolfindchildrenexbyva"></a>IDiaSymbol::findChildrenExByVA
Pobiera elementy podrzędne symbolu, które są prawidłowe na określonym adresie wirtualnym.

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

podczas Określa Tagi symboli elementów podrzędnych, które mają zostać pobrane, zgodnie z definicją w [wyliczeniu SymTagEnum —](../../debugger/debug-interface-access/symtagenum.md). Ustaw na `SymTagNull` dla wszystkich elementów podrzędnych do pobrania.

 `name`

podczas Określa nazwę elementów podrzędnych do pobrania. Ustaw na `NULL` dla wszystkich elementów podrzędnych do pobrania.

 `compareFlags`

podczas Określa opcje porównywania, które mają być stosowane do dopasowywania nazw. Wartości z wyliczenia [namesearchoptions —](../../debugger/debug-interface-access/namesearchoptions.md) można użyć samodzielnie lub w połączeniu.

 `address`

podczas Określa adres wirtualny.

 `ppResult`

określoną Zwraca obiekt [IDiaEnumSymbols](../../debugger/debug-interface-access/idiaenumsymbols.md) , który zawiera listę pobranych symboli podrzędnych.

## <a name="return-value"></a>Wartość zwracana
 Zwraca `S_OK`, jeśli co najmniej jeden element podrzędny symbolu został znaleziony lub zwraca `S_FALSE`, jeśli nie znaleziono żadnych elementów podrzędnych; w przeciwnym razie zwraca kod błędu.

## <a name="remarks"></a>Uwagi
 Zwrócone symbole lokalne obejmują informacje o zakresie aktywnym.

## <a name="requirements"></a>Wymagania
 Nagłówek: dia2. h

 Biblioteka: diaguids. lib

 DLL: msdia100. dll

## <a name="see-also"></a>Zobacz także
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
- [SymTagEnum, wyliczenie](../../debugger/debug-interface-access/symtagenum.md)
- [IDiaEnumSymbols](../../debugger/debug-interface-access/idiaenumsymbols.md)
- [IDiaSession::findChildren](../../debugger/debug-interface-access/idiasession-findchildren.md)
- [NameSearchOptions, wyliczenie](../../debugger/debug-interface-access/namesearchoptions.md)