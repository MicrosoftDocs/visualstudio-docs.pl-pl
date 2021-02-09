---
title: 'IDiaSymbol:: findChildrenEx | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::findChildrenEx
ms.assetid: 6e045045-da8c-4338-9423-81a1ca20c405
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 68c13c433d10bb462c78397b012000f0f245327a
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99863719"
---
# <a name="idiasymbolfindchildrenex"></a>IDiaSymbol::findChildrenEx
Pobiera elementy podrzędne symbolu. Symbole lokalne, które są zwracane, zawierają informacje o zakresie aktywnym, jeśli program jest kompilowany z optymalizacją na.

## <a name="syntax"></a>Składnia

```C++
HRESULT findChildrenEx ( 
   enum SymTagEnum   symtag,
   LPCOLESTR         name,
   DWORD             compareFlags,
   IDiaEnumSymbols** ppResult
);
```

#### <a name="parameters"></a>Parametry
 `symtag`

podczas Określa Tagi symboli elementów podrzędnych, które mają zostać pobrane, zgodnie z definicją w [wyliczeniu SymTagEnum —](../../debugger/debug-interface-access/symtagenum.md). Ustaw na `SymTagNull` wszystkie elementy podrzędne do pobrania.

 `name`

podczas Określa nazwę elementów podrzędnych do pobrania. Ustaw na `NULL` wszystkie elementy podrzędne do pobrania.

 `compareFlags`

podczas Określa opcje porównywania, które mają być stosowane do dopasowywania nazw. Wartości z wyliczenia [namesearchoptions —](../../debugger/debug-interface-access/namesearchoptions.md) można użyć samodzielnie lub w połączeniu.

 `ppResult`

określoną Zwraca obiekt [IDiaEnumSymbols](../../debugger/debug-interface-access/idiaenumsymbols.md) , który zawiera listę pobranych symboli podrzędnych.

## <a name="return-value"></a>Wartość zwracana
 Zwraca `S_OK` Jeśli co najmniej jeden element podrzędny symbolu został znaleziony lub zwraca, `S_FALSE` Jeśli nie znaleziono żadnych elementów podrzędnych; w przeciwnym razie zwraca kod błędu.

## <a name="remarks"></a>Uwagi
 Ta metoda jest rozszerzoną wersją [IDiaSymbol:: findChildren —](../../debugger/debug-interface-access/idiasymbol-findchildren.md).

## <a name="requirements"></a>Wymagania
 Nagłówek: dia2. h

 Biblioteka: diaguids. lib

 DLL: msdia100.dll

## <a name="see-also"></a>Zobacz też
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
- [SymTagEnum, wyliczenie](../../debugger/debug-interface-access/symtagenum.md)
- [IDiaEnumSymbols](../../debugger/debug-interface-access/idiaenumsymbols.md)
- [IDiaSession::findChildren](../../debugger/debug-interface-access/idiasession-findchildren.md)
- [NameSearchOptions, wyliczenie](../../debugger/debug-interface-access/namesearchoptions.md)