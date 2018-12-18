---
title: Idiaaddressmap — | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- IDiaAddressMap interface
ms.assetid: e6467529-508c-4328-85d7-89444ae4d1c1
caps.latest.revision: 13
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 041b784154ef5c95f75d8574700a65460a0ec663
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/16/2018
ms.locfileid: "51722722"
---
# <a name="idiaaddressmap"></a>IDiaAddressMap
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Zapewnia kontrolę nad jak DIA SDK oblicza względne i wirtualnego wirtualne adresy obiektów debugowania.  
  
## <a name="syntax"></a>Składnia  
  
```  
IDiaAddressMap : IUnknown  
```  
  
## <a name="methods-in-vtable-order"></a>Metody w Vtable kolejności  
 W poniższej tabeli przedstawiono metody `IDiaAddressMap`.  
  
|Metoda|Opis|  
|------------|-----------------|  
|[IDiaAddressMap::get_addressMapEnabled](../../debugger/debug-interface-access/idiaaddressmap-get-addressmapenabled.md)|Wskazuje, czy mapa adresu została ustanowiona dla określonej sesji.|  
|[IDiaAddressMap::put_addressMapEnabled](../../debugger/debug-interface-access/idiaaddressmap-put-addressmapenabled.md)|Określa, czy mapa adresu powinien być używany do translacji adresów symboli.|  
|[IDiaAddressMap::get_relativeVirtualAddressEnabled](../../debugger/debug-interface-access/idiaaddressmap-get-relativevirtualaddressenabled.md)|Wskazuje, czy obliczenia i Użyj względnych adresów wirtualnych jest włączone.|  
|[IDiaAddressMap::put_relativeVirtualAddressEnabled](../../debugger/debug-interface-access/idiaaddressmap-put-relativevirtualaddressenabled.md)|Pozwoli to klientowi włączyć lub wyłączyć obliczanie względnych adresów wirtualnych.|  
|[IDiaAddressMap::get_imageAlign](../../debugger/debug-interface-access/idiaaddressmap-get-imagealign.md)|Pobiera bieżący wyrównanie obrazu.|  
|[IDiaAddressMap::put_imageAlign](../../debugger/debug-interface-access/idiaaddressmap-put-imagealign.md)|Ustawia wyrównanie obrazu.|  
|[IDiaAddressMap::set_imageHeaders](../../debugger/debug-interface-access/idiaaddressmap-set-imageheaders.md)|Ustawia obraz nagłówki, aby włączyć translację względnych adresów wirtualnych.|  
|[IDiaAddressMap::set_addressMap](../../debugger/debug-interface-access/idiaaddressmap-set-addressmap.md)|Zawiera mapę adresu do obsługi obrazów układ tłumaczenia.|  
  
## <a name="remarks"></a>Uwagi  
 Kontrolka udostępniane przez ten interfejs jest hermetyzowany w dwóch zestawów danych, należy podać: obraz nagłówków i eliminowania mapy. Większość klientów użyj [idiadatasource::loaddataforexe —](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md) metodę, aby znaleźć informacje o debugowaniu właściwe dla obrazu, a także metoda zazwyczaj mogą odnajdywać wszystkie niezbędne nagłówki oraz maps samych danych. Jednak niektórzy klienci zaimplementować wyspecjalizowanych przetwarzania i wyszukiwanie danych. Takich klientów należy użyć metod `IDiaAddressMap` interfejsu, aby zapewnić DIA SDK w wynikach wyszukiwania.  
  
## <a name="notes-for-callers"></a>Uwagi dotyczące wywoływania  
 Ten interfejs jest dostępny z obiektu session DIA. Wywołania klienta `QueryInterface` metoda DIA sesji obiektu interfejsu, zwykle [idiasession —](../../debugger/debug-interface-access/idiasession.md), aby pobrać `IDiaAddressMap` interfejsu.  
  
## <a name="requirements"></a>Wymagania  
 Nagłówek: Dia2.h  
  
 Biblioteka: diaguids.lib  
  
 Biblioteki DLL: msdia80.dll  
  
## <a name="see-also"></a>Zobacz też  
 [Interfejsy (debugowanie zestaw SDK dostępu do interfejsu)](../../debugger/debug-interface-access/interfaces-debug-interface-access-sdk.md)   
 [Idiadatasource::loaddataforexe —](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md)   
 [IDiaSession](../../debugger/debug-interface-access/idiasession.md)



