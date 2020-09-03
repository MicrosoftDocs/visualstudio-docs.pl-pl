---
title: 'IDiaAddressMap:: set_addressMap | Microsoft Docs'
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "68198651"
---
# <a name="idiaaddressmapset_addressmap"></a>IDiaAddressMap::set_addressMap
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Udostępnia mapę adresów do obsługi tłumaczenia układu obrazu.  
  
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
 podczas Liczba elementów w `data` parametrze.  
  
 `data[]`  
 podczas Tablica struktur [struktury DiaAddressMapEntry —](../../debugger/debug-interface-access/diaaddressmapentry.md) , które definiują mapę translacji.  
  
 `imagetoSymbols`  
 [w] `TRUE` Jeśli `data` parametr definiuje mapę z nowego układu obrazu do oryginalnego układu (zgodnie z opisem przez symbole debugowania). `FALSE` Jeśli `data` jest mapą do nowego układu obrazu pobranego z oryginalnego układu.  
  
## <a name="return-value"></a>Wartość zwracana  
 Jeśli powiedzie się, zwraca `S_OK` ; w przeciwnym razie zwraca kod błędu.  
  
## <a name="remarks"></a>Uwagi  
 Zazwyczaj DIA Pobiera mapowania translacji adresów z pliku bazy danych programu (. pdb). Jeśli brakuje tych wartości, Metoda [IDiaAddressMap:: set_imageHeaders](../../debugger/debug-interface-access/idiaaddressmap-set-imageheaders.md) jest wywoływana dwukrotnie, raz z `imagetoSymbols` parametrem ustawionym na `TRUE` i jeden raz z `imagetoSymbols` parametrem ustawionym na `FALSE` . Nie można włączyć translacji mapowania adresów przy użyciu metody [IDiaAddressMap::p ut_addressMapEnabled](../../debugger/debug-interface-access/idiaaddressmap-put-addressmapenabled.md) , chyba że podano oba mapy tłumaczeń.  
  
## <a name="see-also"></a>Zobacz też  
 [DiaAddressMapEntry —, struktura](../../debugger/debug-interface-access/diaaddressmapentry.md)   
 [IDiaAddressMap](../../debugger/debug-interface-access/idiaaddressmap.md)   
 [IDiaAddressMap::p ut_addressMapEnabled](../../debugger/debug-interface-access/idiaaddressmap-put-addressmapenabled.md)   
 [IDiaAddressMap::set_imageHeaders](../../debugger/debug-interface-access/idiaaddressmap-set-imageheaders.md)
