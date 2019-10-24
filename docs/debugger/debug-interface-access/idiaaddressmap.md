---
title: IDiaAddressMap | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaAddressMap interface
ms.assetid: e6467529-508c-4328-85d7-89444ae4d1c1
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 7e06acf045ce1893762d5c898752dd6bc40de50a
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/22/2019
ms.locfileid: "72744989"
---
# <a name="idiaaddressmap"></a>IDiaAddressMap
Zapewnia kontrolę nad sposobem, w jaki DIA SDK oblicza wirtualne i względne adresy wirtualne dla obiektów debugowania.

## <a name="syntax"></a>Składnia

```
IDiaAddressMap : IUnknown
```

## <a name="methods-in-vtable-order"></a>Metody w kolejności tablic wirtualnych
 W poniższej tabeli przedstawiono metody `IDiaAddressMap`.

|Metoda|Opis|
|------------|-----------------|
|[IDiaAddressMap::get_addressMapEnabled](../../debugger/debug-interface-access/idiaaddressmap-get-addressmapenabled.md)|Wskazuje, czy mapa adresów została ustanowiona dla konkretnej sesji.|
|[IDiaAddressMap::put_addressMapEnabled](../../debugger/debug-interface-access/idiaaddressmap-put-addressmapenabled.md)|Określa, czy mapa adresów ma być używana do tłumaczenia adresów symboli.|
|[IDiaAddressMap::get_relativeVirtualAddressEnabled](../../debugger/debug-interface-access/idiaaddressmap-get-relativevirtualaddressenabled.md)|Wskazuje, czy jest włączone Obliczanie i użycie względnych adresów wirtualnych.|
|[IDiaAddressMap::put_relativeVirtualAddressEnabled](../../debugger/debug-interface-access/idiaaddressmap-put-relativevirtualaddressenabled.md)|Zezwala klientowi na włączanie lub wyłączanie obliczeń względnych adresów wirtualnych.|
|[IDiaAddressMap::get_imageAlign](../../debugger/debug-interface-access/idiaaddressmap-get-imagealign.md)|Pobiera bieżące wyrównanie obrazu.|
|[IDiaAddressMap::put_imageAlign](../../debugger/debug-interface-access/idiaaddressmap-put-imagealign.md)|Ustawia wyrównanie obrazu.|
|[IDiaAddressMap::set_imageHeaders](../../debugger/debug-interface-access/idiaaddressmap-set-imageheaders.md)|Ustawia nagłówki obrazu w celu włączenia tłumaczenia względnych adresów wirtualnych.|
|[IDiaAddressMap::set_addressMap](../../debugger/debug-interface-access/idiaaddressmap-set-addressmap.md)|Udostępnia mapę adresów do obsługi tłumaczenia układu obrazu.|

## <a name="remarks"></a>Uwagi
 Kontrolka udostępniana przez ten interfejs jest hermetyzowana w dwóch zestawach danych, które dostarczasz: nagłówki i mapowania adresów obrazu. Większość klientów używa metody [IDiaDataSource:: loadDataForExe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md) , aby znaleźć odpowiednie informacje debugowania dla obrazu, a metoda zazwyczaj może wykryć wszystkie wymagane nagłówki i mapować same dane. Jednak niektórzy klienci implementują wyspecjalizowane przetwarzanie i wyszukują dane. Tacy klienci używają metod interfejsu `IDiaAddressMap`, aby zapewnić DIA SDK z wynikami wyszukiwania.

## <a name="notes-for-callers"></a>Uwagi dotyczące wywoływania
 Ten interfejs jest dostępny w obiekcie sesji DIA. Klient wywołuje metodę `QueryInterface` w interfejsie obiektu sesji DIA, zwykle [IDiaSession](../../debugger/debug-interface-access/idiasession.md), aby pobrać interfejs `IDiaAddressMap`.

## <a name="requirements"></a>Wymagania
 Nagłówek: dia2. h

 Biblioteka: diaguids. lib

 DLL: msdia80. dll

## <a name="see-also"></a>Zobacz także
- [Interfejsy (Zestaw SDK dostępu do interfejsu debugowania)](../../debugger/debug-interface-access/interfaces-debug-interface-access-sdk.md)
- [IDiaDataSource::loadDataForExe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md)
- [IDiaSession](../../debugger/debug-interface-access/idiasession.md)