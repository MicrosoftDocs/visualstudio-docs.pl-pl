---
title: 'IDiaSymbol:: get_frontEndMinor | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_frontEndMinor method
ms.assetid: 40792153-827c-4859-be7c-6aa16d5abab6
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 2b329cd69d010cba4e3667bde0d7b976389037bb
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/22/2019
ms.locfileid: "72740647"
---
# <a name="idiasymbolget_frontendminor"></a>IDiaSymbol::get_frontEndMinor
Pobiera numer wersji pomocniczej frontonu.

## <a name="syntax"></a>Składnia

```C++
HRESULT get_frontEndMinor ( 
   DWORD* pRetVal
);
```

#### <a name="parameters"></a>Parametry
 `pRetVal`

określoną Zwraca pierwszy podrzędny numer wersji.

## <a name="return-value"></a>Wartość zwracana
 Jeśli powiedzie się, zwraca `S_OK`; w przeciwnym razie zwraca `S_FALSE` lub kod błędu.

> [!NOTE]
> Wartość zwracana `S_FALSE` oznacza, że właściwość nie jest dostępna dla symbolu.

## <a name="remarks"></a>Uwagi
 Kompilator zwykle składa się z dwóch głównych elementów: fronton (Parser), który obsługuje Analizowanie kodu źródłowego w postaci pośredniej i zaplecza (Generator kodu), który konwertuje pośredni formularz do zestawu. Nie zdarza się, że fronton nie ma innej wersji niż zaplecze.

 Numer wersji frontonu lub zaplecza składa się z trzech części: \<major >. > \<minor. \<build >, gdzie \<major > jest głównym numerem wersji, \<minor > jest numerem wersji pomocniczej, a \<build > jest numerem kompilacji. Na przykład 13.10.3077.

## <a name="requirements"></a>Wymagania

|Wymaganie|Opis|
|-----------------|-----------------|
|Nagłówki|dia2. h|
|Wersja:|DIA SDK v 7.0|

## <a name="see-also"></a>Zobacz także
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)