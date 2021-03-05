---
description: Pobiera wszystkie elementy podrzędne określonego identyfikatora nadrzędnego, które pasują do nazwy i typu symbolu.
title: 'IDiaSession:: findChildren — | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSession::findChildren method
ms.assetid: 5d19046f-f668-4aa9-8788-95cda9a98997
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: ea45a427b00d7627eaba21bdd628f2cff2cefbf0
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/05/2021
ms.locfileid: "102147869"
---
# <a name="idiasessionfindchildren"></a>IDiaSession::findChildren
Pobiera wszystkie elementy podrzędne określonego identyfikatora nadrzędnego, które pasują do nazwy i typu symbolu.

## <a name="syntax"></a>Składnia

```C++
HRESULT findChildren ( 
   IDiaSymbol*       parent,
   SymTagEnum        symtag,
   LPCOLESTR         name,
   DWORD             compareFlags,
   IDiaEnumSymbols** ppResult
);
```

#### <a name="parameters"></a>Parametry
 `parent`

podczas Obiekt [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md) reprezentujący element nadrzędny. Jeśli ten symbol nadrzędny jest funkcją, modułem lub blokiem, wówczas jego leksykalne elementy podrzędne są zwracane w `ppResult` . Jeśli symbol nadrzędny jest typem, jego elementy podrzędne klasy są zwracane. Jeśli ten parametr ma wartość `NULL` , `symtag` musi być ustawiona na `SymTagExe` lub `SymTagNull` , która zwraca zakres globalny (plik. exe).

 `symtag`

podczas Określa tag symbolu elementów podrzędnych, które mają zostać pobrane. Wartości są pobierane z wyliczenia [wyliczenia SymTagEnum —](../../debugger/debug-interface-access/symtagenum.md) . Ustaw, aby `SymTagNull` pobrać wszystkie elementy podrzędne.

 `name`

podczas Określa nazwę elementów podrzędnych do pobrania. Ustaw na `NULL` wszystkie elementy podrzędne do pobrania.

 `compareFlags`

podczas Określa opcje porównania stosowane do dopasowywania nazw. Wartości z wyliczenia [namesearchoptions —](../../debugger/debug-interface-access/namesearchoptions.md) można użyć samodzielnie lub w połączeniu.

 `ppResult`

określoną Zwraca obiekt [IDiaEnumSymbols](../../debugger/debug-interface-access/idiaenumsymbols.md) , który zawiera listę pobranych symboli podrzędnych.

## <a name="return-value"></a>Wartość zwracana
 Jeśli powiedzie się, zwraca `S_OK` ; w przeciwnym razie zwraca kod błędu.

## <a name="example"></a>Przykład
 Poniższy przykład pokazuje, jak znaleźć zmienne lokalne funkcji `pFunc` , które pasują do nazwy `szVarName` .

```C++
IDiaEnumSymbols* pEnum;
pSession->findChildren( pFunc, SymTagData, szVarName, nsCaseSensitive, &pEnum );
```

## <a name="see-also"></a>Zobacz też
- [Omówienie](../../debugger/debug-interface-access/overview-debug-interface-access-sdk.md)
- [IDiaEnumSymbols](../../debugger/debug-interface-access/idiaenumsymbols.md)
- [IDiaSession](../../debugger/debug-interface-access/idiasession.md)
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
- [NameSearchOptions, wyliczenie](../../debugger/debug-interface-access/namesearchoptions.md)
- [SymTagEnum, wyliczenie](../../debugger/debug-interface-access/symtagenum.md)
