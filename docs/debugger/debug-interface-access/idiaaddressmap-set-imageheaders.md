---
title: Idiaaddressmap::set_imageheaders — | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaAddressMap::set_imageHeaders method
ms.assetid: a46b9d0e-43e6-433f-b2c7-aa203981e4e4
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 6593092fc155a375480f082a1f82dc53a1d851fa
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/02/2019
ms.locfileid: "53834142"
---
# <a name="idiaaddressmapsetimageheaders"></a>IDiaAddressMap::set_imageHeaders
Ustawia obraz nagłówki, aby włączyć translację względny adres wirtualny.  
  
## <a name="syntax"></a>Składnia  
  
```C++  
HRESULT set_imageHeaders (   
   DWORD cbData,  
   BYTE  data[],  
   BOOL  originalHeaders  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 cbData  
 [in] Liczba bajtów danych w nagłówkach. Musi być `n*sizeof(IMAGE_SECTION_HEADER)` gdzie `n` jest liczba nagłówki sekcji w pliku wykonywalnym.  
  
 dane]  
 [in] Tablica `IMAGE_SECTION_HEADER` struktur, które ma być używany jako nagłówki obrazu.  
  
 originalHeaders  
 [in] Ustaw `FALSE` w przypadku nagłówków obrazu z nowego obrazu `TRUE` jeśli odzwierciedlają oryginalnego obrazu, przed uaktualnieniem. Zwykle będzie to ustawienie `TRUE` tylko w połączeniu z wywołania [idiaaddressmap::set_addressmap —](../../debugger/debug-interface-access/idiaaddressmap-set-addressmap.md) metody.  
  
## <a name="return-value"></a>Wartość zwracana  
 Jeśli operacja się powiedzie, zwraca `S_OK`; w przeciwnym razie zwraca kod błędu.  
  
## <a name="remarks"></a>Uwagi  
 `IMAGE_SECTION_HEADER` Struktury jest zadeklarowany w pliku Winnt.h i reprezentuje format Nagłówek sekcji obrazu pliku wykonywalnego.  
  
 Względny adres wirtualny obliczeń zależą od tego `IMAGE_SECTION_HEADER` wartości. Zazwyczaj DIA pobiera je z plik bazy danych (PDB) programu. Jeśli te wartości są spełnione, DIA nie może obliczyć względnych adresów wirtualnych i [idiaaddressmap::get_relativevirtualaddressenabled —](../../debugger/debug-interface-access/idiaaddressmap-get-relativevirtualaddressenabled.md) metoda zwraca `FALSE`. Następnie należy wywołać klienta [idiaaddressmap::put_relativevirtualaddressenabled —](../../debugger/debug-interface-access/idiaaddressmap-put-relativevirtualaddressenabled.md) metodę umożliwiającą włączenie obliczeń względny adres wirtualny po podaniu brakujących nagłówków obrazu z samego obrazu.  
  
## <a name="see-also"></a>Zobacz też  
 [Idiaaddressmap —](../../debugger/debug-interface-access/idiaaddressmap.md)   
 [Idiaaddressmap::set_addressmap —](../../debugger/debug-interface-access/idiaaddressmap-set-addressmap.md)   
 [Idiaaddressmap::get_relativevirtualaddressenabled —](../../debugger/debug-interface-access/idiaaddressmap-get-relativevirtualaddressenabled.md)   
 [IDiaAddressMap::put_relativeVirtualAddressEnabled](../../debugger/debug-interface-access/idiaaddressmap-put-relativevirtualaddressenabled.md)