---
title: 'IDiaSymbol:: findChildrenExByRVA | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::findChildrenExByRVA
ms.assetid: cbc57c6c-7d64-4469-a114-1dd6671e5ec5
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 936aa9006fac088efbb155d44ca8e4257ce94302
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "85464570"
---
# <a name="idiasymbolfindchildrenexbyrva"></a>IDiaSymbol::findChildrenExByRVA
Pobiera elementy podrzędne symbolu, które są prawidłowe w określonym względnym adresie wirtualnym (RVA).

## <a name="syntax"></a>Składnia

```C++
HRESULT findChildrenExByRVA ( 
   enum SymTagEnum   symtag,
   LPCOLESTR         name,
   DWORD             compareFlags,
   DWORD             address,
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

 `address`

podczas Określa adres RVA.

 `ppResult`

określoną Zwraca obiekt [IDiaEnumSymbols](../../debugger/debug-interface-access/idiaenumsymbols.md) , który zawiera listę pobranych symboli podrzędnych.

## <a name="return-value"></a>Wartość zwracana
 Zwraca `S_OK` Jeśli co najmniej jeden element podrzędny symbolu został znaleziony lub zwraca, `S_FALSE` Jeśli nie znaleziono żadnych elementów podrzędnych; w przeciwnym razie zwraca kod błędu.

## <a name="remarks"></a>Uwagi
 Zwrócone symbole lokalne obejmują informacje o zakresie aktywnym.

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