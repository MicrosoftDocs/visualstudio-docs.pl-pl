---
title: 'IDiaSymbol:: get_frontEndMajor | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_frontEndMajor method
ms.assetid: f8a067c5-3306-4fc5-bc20-8910a47ed504
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 14d69d617d76ffe033e3ab763cdf85dad871f1f5
ms.sourcegitcommit: 66f31cc4ce1236e638ab58d2f70d3646206386fa
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/27/2020
ms.locfileid: "85463884"
---
# <a name="idiasymbolget_frontendmajor"></a>IDiaSymbol::get_frontEndMajor
Pobiera główny numer wersji frontonu.

## <a name="syntax"></a>Składnia

```C++
HRESULT get_frontEndMajor ( 
   DWORD* pRetVal
);
```

#### <a name="parameters"></a>Parametry
 `pRetVal`

określoną Zwraca główny numer wersji frontonu. Zobacz uwagi.

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