---
title: 'IDiaSymbol:: get_addressOffset | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
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
ms.openlocfilehash: 5971b5d7cf55e75c3350c72575856326be62feba
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "85464374"
---
# <a name="idiasymbolget_addressoffset"></a>IDiaSymbol::get_addressOffset
Pobiera część przesunięcia lokalizacji adresu. Użyj, gdy dla [wyliczenia lokalizacji](../../debugger/debug-interface-access/locationtype.md) określono wartość `LocIsStatic` .

## <a name="syntax"></a>Składnia

```C++
HRESULT get_addressOffset ( 
   DWORD* pRetVal
);
```

#### <a name="parameters"></a>Parametry
 `pRetVal`

określoną Zwraca część przesunięcia lokalizacji adresu.

## <a name="return-value"></a>Wartość zwracana
 Jeśli powiedzie się, zwraca `S_OK` ; w przeciwnym razie zwraca `S_FALSE` lub kod błędu.

> [!NOTE]
> Wartość zwracana przez `S_FALSE` oznacza, że właściwość nie jest dostępna dla symbolu.

## <a name="remarks"></a>Uwagi
 W przypadku statycznych elementów członkowskich znajdujących się w zewnętrznej bibliotece DLL przesunięcie zwrócone przez tę metodę może być równe 0, ponieważ ta metoda polega na uzyskaniu adresu wirtualnego elementu członkowskiego. Adresy wirtualne są prawidłowe tylko wtedy, gdy metoda [IDiaSession::p ut_loadAddress](../../debugger/debug-interface-access/idiasession-put-loadaddress.md) w interfejsie [IDiaSession](../../debugger/debug-interface-access/idiasession.md) została wywołana z niezerowym parametrem OKREŚLAJĄCYM adres ładowania biblioteki DLL.

 Aby uzyskać część sekcji adresu, wywołaj metodę [IDiaSymbol:: get_addressSection](../../debugger/debug-interface-access/idiasymbol-get-addresssection.md) .

## <a name="requirements"></a>Wymagania

|Wymaganie|Opis|
|-----------------|-----------------|
|Nagłówki|dia2. h|
|Wersja:|DIA SDK v 7.0|

## <a name="see-also"></a>Zobacz też
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
- [LocationType, wyliczenie](../../debugger/debug-interface-access/locationtype.md)
- [IDiaSymbol::get_addressSection](../../debugger/debug-interface-access/idiasymbol-get-addresssection.md)
- [IDiaSession::put_loadAddress](../../debugger/debug-interface-access/idiasession-put-loadaddress.md)
- [IDiaSession](../../debugger/debug-interface-access/idiasession.md)