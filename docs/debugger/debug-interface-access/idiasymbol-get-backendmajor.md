---
title: Idiasymbol::get_backendmajor — | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_backEndMajor method
ms.assetid: 900a05dd-c29b-44ad-b46b-f43bda819a66
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 7371bf097e0eb10442075a45fddb9b924a3a93b3
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/21/2019
ms.locfileid: "56615328"
---
# <a name="idiasymbolgetbackendmajor"></a>IDiaSymbol::get_backEndMajor
Pobiera zaplecza główny numer wersji kompilatora.

## <a name="syntax"></a>Składnia

```C++
HRESULT get_backEndMajor ( 
   DWORD* pRetVal
);
```

#### <a name="parameters"></a>Parametry
 `pRetVal`

[out] Zwraca numer wersji głównej zaplecza. Zobacz uwagi.

## <a name="return-value"></a>Wartość zwracana
 Jeśli operacja się powiedzie, zwraca `S_OK`; w przeciwnym razie zwraca `S_FALSE` lub kod błędu.

> [!NOTE]
>  Zwracana wartość wynosząca `S_FALSE` oznacza, że właściwość nie jest dostępna dla symbolu.

## <a name="remarks"></a>Uwagi
 Kompilatora zwykle składa się z dwóch podstawowe elementy: fronton (analizatora), która obsługuje analizowania kodu źródłowego w formie pośredniego, i zapleczem (generator kodu) konwertująca pośrednich formularza do zestawu. Nie jest niczym niezwykłym frontonu do innej wersji niż zaplecza.

 Frontonu lub zaplecza numer wersji składa się z trzech części: \<główna >.\< pomocnicza >. \<kompilacji >, gdzie \<główne > jest główny numer wersji, \<pomocnicza > jest numerem wersji pomocniczej i \<kompilacji > jest numerem kompilacji. Na przykład 13.10.3077.

## <a name="requirements"></a>Wymagania

|Wymaganie|Opis|
|-----------------|-----------------|
|Nagłówek:|dia2.h|
|Wersja:|V7.0 DIA SDK|

## <a name="see-also"></a>Zobacz też
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)