---
description: Pobiera część sekcji lokalizacji adresowej.
title: 'IDiaSymbol:: get_addressSection | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_addressSection method
ms.assetid: fe80d479-3bb5-4f55-9b62-1bd58d0a60ce
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 3e0b6554011a29a7b90d1d7c55deefced01b27c3
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/05/2021
ms.locfileid: "102156588"
---
# <a name="idiasymbolget_addresssection"></a>IDiaSymbol::get_addressSection
Pobiera część sekcji lokalizacji adresowej. Użyj, gdy dla [wyliczenia lokalizacji](../../debugger/debug-interface-access/locationtype.md) określono wartość `LocIsStatic` .

## <a name="syntax"></a>Składnia

```C++
HRESULT get_addressSection ( 
   DWORD* pRetVal
);
```

#### <a name="parameters"></a>Parametry
 `pRetVal`

określoną Zwraca część sekcji lokalizacji adresowej.

## <a name="return-value"></a>Wartość zwracana
 Jeśli powiedzie się, zwraca `S_OK` ; w przeciwnym razie zwraca `S_FALSE` lub kod błędu.

> [!NOTE]
> Wartość zwracana przez `S_FALSE` oznacza, że właściwość nie jest dostępna dla symbolu.

## <a name="remarks"></a>Uwagi
 W przypadku statycznych elementów członkowskich znajdujących się w zewnętrznej bibliotece DLL sekcja zwracana przez tę metodę może być równa 0, ponieważ ta metoda polega na uzyskaniu adresu wirtualnego elementu członkowskiego. Adresy wirtualne są prawidłowe tylko wtedy, gdy metoda [IDiaSession::p ut_loadAddress](../../debugger/debug-interface-access/idiasession-put-loadaddress.md) w interfejsie [IDiaSession](../../debugger/debug-interface-access/idiasession.md) została wywołana z niezerowym parametrem OKREŚLAJĄCYM adres ładowania biblioteki DLL.

 Aby uzyskać część przesunięcia adresu, wywołaj metodę [IDiaSymbol:: get_addressOffset](../../debugger/debug-interface-access/idiasymbol-get-addressoffset.md) .

## <a name="requirements"></a>Wymagania

|Wymaganie|Opis|
|-----------------|-----------------|
|Nagłówki|dia2. h|
|Wersja:|DIA SDK v 7.0|

## <a name="see-also"></a>Zobacz też
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
- [LocationType, wyliczenie](../../debugger/debug-interface-access/locationtype.md)
