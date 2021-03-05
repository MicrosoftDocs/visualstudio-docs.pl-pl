---
description: Pobiera określoną liczbę symboli w sekwencji wyliczenia.
title: 'IDiaEnumSymbols:: Next | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumSymbols::Next method
ms.assetid: bfe5fe27-6a84-4392-910f-e325146d7552
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: f1effa2d3b861be076a18adaaeafa10549ec7478
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/05/2021
ms.locfileid: "102148711"
---
# <a name="idiaenumsymbolsnext"></a>IDiaEnumSymbols::Next
Pobiera określoną liczbę symboli w sekwencji wyliczenia.

## <a name="syntax"></a>Składnia

```C++
HRESULT Next ( 
   ULONG        celt,
   IDiaSymbol** rgelt,
   ULONG*       pceltFetched
);
```

#### <a name="parameters"></a>Parametry
 celt

podczas Liczba symboli w module wyliczającym do pobrania.

 rgelt

określoną Tablica, która ma zostać wypełniona obiektami [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md) , które reprezentują żądane symbole.

 pceltFetched

określoną Zwraca liczbę symboli w ramach pobranego modułu wyliczającego.

## <a name="return-value"></a>Wartość zwracana
 Jeśli powiedzie się, zwraca `S_OK` . Zwraca `S_FALSE` czy nie ma więcej symboli. W przeciwnym razie zwraca kod błędu.

## <a name="example"></a>Przykład

```C++
IDiaEnumSymbols* pEnum
CComPtr< IDiaSymbol> pSym;
DWORD celt;
pEnum->Next( 1, &pSym, &celt );
```

## <a name="see-also"></a>Zobacz także
- [IDiaEnumSymbols](../../debugger/debug-interface-access/idiaenumsymbols.md)
- [IDiaSession::findLinesByLinenum](../../debugger/debug-interface-access/idiasession-findlinesbylinenum.md)
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
