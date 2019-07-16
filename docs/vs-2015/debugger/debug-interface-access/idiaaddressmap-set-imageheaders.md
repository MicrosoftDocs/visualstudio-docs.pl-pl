---
title: Idiaaddressmap::set_imageheaders — | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaAddressMap::set_imageHeaders method
ms.assetid: a46b9d0e-43e6-433f-b2c7-aa203981e4e4
caps.latest.revision: 10
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 18fa69929f78d5ae661169a09db97697d98f4d94
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "68198641"
---
# <a name="idiaaddressmapsetimageheaders"></a>IDiaAddressMap::set_imageHeaders
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Ustawia obraz nagłówki, aby włączyć translację względny adres wirtualny.  
  
## <a name="syntax"></a>Składnia  
  
```cpp#  
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
 [IDiaAddressMap](../../debugger/debug-interface-access/idiaaddressmap.md)   
 [IDiaAddressMap::set_addressMap](../../debugger/debug-interface-access/idiaaddressmap-set-addressmap.md)   
 [IDiaAddressMap::get_relativeVirtualAddressEnabled](../../debugger/debug-interface-access/idiaaddressmap-get-relativevirtualaddressenabled.md)   
 [IDiaAddressMap::put_relativeVirtualAddressEnabled](../../debugger/debug-interface-access/idiaaddressmap-put-relativevirtualaddressenabled.md)
