---
title: Idiasymbol::get_addresssection — | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_addressSection method
ms.assetid: fe80d479-3bb5-4f55-9b62-1bd58d0a60ce
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: f24bd9c4a541caad54f963a4ea2924e80846e80d
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/21/2019
ms.locfileid: "56632293"
---
# <a name="idiasymbolgetaddresssection"></a>IDiaSymbol::get_addressSection
Pobiera część sekcji adres lokalizacji. Zastosowania [locationtype — wyliczenie](../../debugger/debug-interface-access/locationtype.md) ustawiono `LocIsStatic`.

## <a name="syntax"></a>Składnia

```C++
HRESULT get_addressSection ( 
   DWORD* pRetVal
);
```

#### <a name="parameters"></a>Parametry
 `pRetVal`

[out] Zwraca część sekcji adres lokalizacji.

## <a name="return-value"></a>Wartość zwracana
 Jeśli operacja się powiedzie, zwraca `S_OK`; w przeciwnym razie zwraca `S_FALSE` albo kod błędu.

> [!NOTE]
>  Zwracana wartość wynosząca `S_FALSE` oznacza, że właściwość nie jest dostępna dla symbolu.

## <a name="remarks"></a>Uwagi
 Dla statycznych elementów członkowskich znajdujących się w zewnętrznej bibliotece DLL sekcja zwracanego przez tę metodę może mieć wartość 0, ponieważ ta metoda zależy od tego, uzyskiwanie adresu wirtualnego elementu członkowskiego. Wirtualne adresy są prawidłowe tylko wtedy, gdy [idiasession::put_loadaddress —](../../debugger/debug-interface-access/idiasession-put-loadaddress.md) method in Class metoda [idiasession —](../../debugger/debug-interface-access/idiasession.md) interfejsu została wywołana z parametrem wartość różną od zera, określając adres obciążenia biblioteki dll.

 Aby uzyskać przesunięcia część adresu, należy wywołać [idiasymbol::get_addressoffset —](../../debugger/debug-interface-access/idiasymbol-get-addressoffset.md) metody.

## <a name="requirements"></a>Wymagania

|Wymaganie|Opis|
|-----------------|-----------------|
|Nagłówek:|dia2.h|
|Wersja:|V7.0 DIA SDK|

## <a name="see-also"></a>Zobacz też
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
- [LocationType, wyliczenie](../../debugger/debug-interface-access/locationtype.md)