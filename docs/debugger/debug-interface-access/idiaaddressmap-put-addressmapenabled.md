---
title: IDiaAddressMap::put_addressMapEnabled | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaAddressMap::put_addressMapEnabled method
ms.assetid: 0f205337-4e59-4383-8059-7b1d207d6dcd
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: a53d66879155ae1ce2cd831c029bc5776a7dd863
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/25/2019
ms.locfileid: "54999213"
---
# <a name="idiaaddressmapputaddressmapenabled"></a>IDiaAddressMap::put_addressMapEnabled
Określa, czy mapa adresu powinien być używany do translacji adresów symboli.  
  
## <a name="syntax"></a>Składnia  
  
```C++  
HRESULT put_addressMapEnabled (   
   BOOL NewVal  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 NewVal  
 [in] Ustaw `TRUE` Aby włączyć translację symboli, lub `FALSE` można wyłączyć.  
  
## <a name="return-value"></a>Wartość zwracana  
 Jeśli operacja się powiedzie, zwraca `S_OK`; w przeciwnym razie zwraca kod błędu.  
  
## <a name="remarks"></a>Uwagi  
 Wykonywalny procesorów po aktualizacji czasami pliku wykonywalnego. DIA zawiera mechanizm obsługi tłumaczenia symboli do nowego układu.  
  
 Po załadowaniu pliku PDB, przechowywane w pliku mapy adresów jest włączona. Czasami jednak gdy aplikacja kliencka może być konieczne podanie własnej mapy adresów przez wywołanie metody [idiaaddressmap::set_addressmap —](../../debugger/debug-interface-access/idiaaddressmap-set-addressmap.md) metody. Jeśli `set_addressMap` metoda zakończy się powodzeniem, aplikacja kliencka musi wywołać `put_addressMapEnabled` metody z `NewVal` parametru `TRUE` umożliwia korzystanie z tej mapy adresów.  
  
 Bieżący stan mapowania adresów włączane mogą być pobierane z wywołaniem [idiaaddressmap::get_addressmapenabled —](../../debugger/debug-interface-access/idiaaddressmap-get-addressmapenabled.md) metody.  
  
## <a name="see-also"></a>Zobacz też  
 [IDiaAddressMap](../../debugger/debug-interface-access/idiaaddressmap.md)   
 [IDiaAddressMap::set_addressMap](../../debugger/debug-interface-access/idiaaddressmap-set-addressmap.md)   
 [IDiaAddressMap::get_addressMapEnabled](../../debugger/debug-interface-access/idiaaddressmap-get-addressmapenabled.md)