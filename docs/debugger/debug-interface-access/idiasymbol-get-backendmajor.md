---
title: 'IDiaSymbol:: get_backEndMajor | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_backEndMajor method
ms.assetid: 900a05dd-c29b-44ad-b46b-f43bda819a66
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 725e08bbe9ae41dc44fb90033bec994a9ca45ab6
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99863565"
---
# <a name="idiasymbolget_backendmajor"></a>IDiaSymbol::get_backEndMajor
Pobiera główny numer wersji kompilatora.

## <a name="syntax"></a>Składnia

```C++
HRESULT get_backEndMajor ( 
   DWORD* pRetVal
);
```

#### <a name="parameters"></a>Parametry
 `pRetVal`

określoną Zwraca główny numer wersji. Zobacz uwagi.

## <a name="return-value"></a>Wartość zwracana
 Jeśli powiedzie się, zwraca `S_OK` ; w przeciwnym razie zwraca `S_FALSE` lub kod błędu.

> [!NOTE]
> Wartość zwracana przez `S_FALSE` oznacza, że właściwość nie jest dostępna dla symbolu.

## <a name="remarks"></a>Uwagi
 Kompilator zwykle składa się z dwóch głównych elementów: fronton (Parser), który obsługuje Analizowanie kodu źródłowego w postaci pośredniej i zaplecza (Generator kodu), który konwertuje pośredni formularz do zestawu. Nie zdarza się, że fronton nie ma innej wersji niż zaplecze.

 Numer wersji frontonu lub zaplecza składa się z trzech części: \<major> . \<minor> . \<build> , gdzie \<major> jest głównym numerem wersji, \<minor> jest numerem wersji pomocniczej i \<build> jest numerem kompilacji. Na przykład 13.10.3077.

## <a name="requirements"></a>Wymagania

|Wymaganie|Opis|
|-----------------|-----------------|
|Nagłówki|dia2. h|
|Wersja:|DIA SDK v 7.0|

## <a name="see-also"></a>Zobacz też
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)