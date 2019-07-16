---
title: IDiaAddressMap::set_addressMap | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaAddressMap::set_addressMap method
ms.assetid: 81e82073-089b-43d5-af39-49d7a4907c7a
caps.latest.revision: 12
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 693ecf6e8fd4f0b55936bde371b7baa6975b8f2c
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "68198651"
---
# <a name="idiaaddressmapsetaddressmap"></a>IDiaAddressMap::set_addressMap
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Zawiera mapę adresu do obsługi obrazów układ tłumaczenia.  
  
## <a name="syntax"></a>Składnia  
  
```cpp#  
HRESULT set_addressMap (   
   DWORD                     cbData,  
   struct DiaAddressMapEntry data[],  
   BOOL                      imagetoSymbols  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `cbData`  
 [in] Liczba elementów w `data` parametru.  
  
 `data[]`  
 [in] Tablica [diaaddressmapentry — struktura](../../debugger/debug-interface-access/diaaddressmapentry.md) struktur, które definiują mapy tłumaczenia.  
  
 `imagetoSymbols`  
 [in] `TRUE` Jeśli `data` parametr określa mapowanie z nowego układu obrazu do oryginalnego układu (zgodnie z opisem, za pomocą symboli debugowania). `FALSE` Jeśli `data` mapy do nowego układu obrazu z oryginalnego układu.  
  
## <a name="return-value"></a>Wartość zwracana  
 Jeśli operacja się powiedzie, zwraca `S_OK`; w przeciwnym razie zwraca kod błędu.  
  
## <a name="remarks"></a>Uwagi  
 Zazwyczaj DIA pobiera mapy translacji adresów z plik bazy danych (PDB) programu. Jeśli te wartości są spełnione, [idiaaddressmap::set_imageheaders —](../../debugger/debug-interface-access/idiaaddressmap-set-imageheaders.md) metoda jest wywoływana dwa razy, jeden raz z `imagetoSymbols` parametr `TRUE` i raz przy użyciu `imagetoSymbols` parametr `FALSE`. Translacje mapy adresów nie można włączyć za pomocą [idiaaddressmap::put_addressmapenabled —](../../debugger/debug-interface-access/idiaaddressmap-put-addressmapenabled.md) metody, chyba że znajdują się zarówno mapy tłumaczenia.  
  
## <a name="see-also"></a>Zobacz też  
 [Diaaddressmapentry — struktura](../../debugger/debug-interface-access/diaaddressmapentry.md)   
 [IDiaAddressMap](../../debugger/debug-interface-access/idiaaddressmap.md)   
 [IDiaAddressMap::put_addressMapEnabled](../../debugger/debug-interface-access/idiaaddressmap-put-addressmapenabled.md)   
 [IDiaAddressMap::set_imageHeaders](../../debugger/debug-interface-access/idiaaddressmap-set-imageheaders.md)
