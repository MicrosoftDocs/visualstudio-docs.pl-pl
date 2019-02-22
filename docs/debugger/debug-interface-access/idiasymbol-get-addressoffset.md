---
title: IDiaSymbol::get_addressOffset | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_addressOffset method
ms.assetid: c15639b0-7f37-46c7-891b-40273b7f6319
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 361df287c626861e82607a9e4cf7edf6cab85a5a
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/21/2019
ms.locfileid: "56599885"
---
# <a name="idiasymbolgetaddressoffset"></a>IDiaSymbol::get_addressOffset
Pobiera przesunięcia część adresu. Zastosowania [locationtype — wyliczenie](../../debugger/debug-interface-access/locationtype.md) ustawiono `LocIsStatic`.

## <a name="syntax"></a>Składnia

```C++
HRESULT get_addressOffset ( 
   DWORD* pRetVal
);
```

#### <a name="parameters"></a>Parametry
 `pRetVal`

[out] Zwraca przesunięcia część adresu.

## <a name="return-value"></a>Wartość zwracana
 Jeśli operacja się powiedzie, zwraca `S_OK`; w przeciwnym razie zwraca `S_FALSE` albo kod błędu.

> [!NOTE]
>  Zwracana wartość wynosząca `S_FALSE` oznacza, że właściwość nie jest dostępna dla symbolu.

## <a name="remarks"></a>Uwagi
 Dla statycznych elementów członkowskich znajdujących się w zewnętrznej bibliotece DLL przesunięcie zwracanego przez tę metodę może mieć wartość 0, ponieważ ta metoda zależy od tego, uzyskiwanie adresu wirtualnego elementu członkowskiego. Wirtualne adresy są prawidłowe tylko wtedy, gdy [idiasession::put_loadaddress —](../../debugger/debug-interface-access/idiasession-put-loadaddress.md) method in Class metoda [idiasession —](../../debugger/debug-interface-access/idiasession.md) interfejsu została wywołana z parametrem wartość różną od zera, określając adres obciążenia biblioteki dll.

 Aby uzyskać sekcji część adresu, należy wywołać [idiasymbol::get_addresssection —](../../debugger/debug-interface-access/idiasymbol-get-addresssection.md) metody.

## <a name="requirements"></a>Wymagania

|Wymaganie|Opis|
|-----------------|-----------------|
|Nagłówek:|dia2.h|
|Wersja:|V7.0 DIA SDK|

## <a name="see-also"></a>Zobacz też
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
- [LocationType, wyliczenie](../../debugger/debug-interface-access/locationtype.md)
- [IDiaSymbol::get_addressSection](../../debugger/debug-interface-access/idiasymbol-get-addresssection.md)
- [IDiaSession::put_loadAddress](../../debugger/debug-interface-access/idiasession-put-loadaddress.md)
- [IDiaSession](../../debugger/debug-interface-access/idiasession.md)