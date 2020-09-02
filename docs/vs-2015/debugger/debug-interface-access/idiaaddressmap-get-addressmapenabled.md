---
title: 'IDiaAddressMap:: get_addressMapEnabled | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaAddressMap::get_addressMapEnabled method
ms.assetid: 6183dc5e-befa-4e5a-ae5a-f4aa24f3ed9e
caps.latest.revision: 10
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 0cf874590d6bcf7f259d7a59eee1b81b79ffe1a4
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "68178247"
---
# <a name="idiaaddressmapget_addressmapenabled"></a>IDiaAddressMap::get_addressMapEnabled
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Wskazuje, czy mapa adresów została ustanowiona dla konkretnej sesji.  
  
## <a name="syntax"></a>Składnia  
  
```cpp#  
HRESULT get_addressMapEnabled (   
   BOOL* pRetVal  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 pRetVal  
 określoną Zwraca `TRUE` czy mapowanie adresu jest włączone.  
  
## <a name="return-value"></a>Wartość zwracana  
 Jeśli powiedzie się, zwraca `S_OK` ; w przeciwnym razie zwraca kod błędu.  
  
## <a name="remarks"></a>Uwagi  
 Wykonywalne przetwórcy czasami aktualizują plik wykonywalny. DIA zawiera mechanizm do obsługi tłumaczenia symboli do nowego układu.  
  
 Aplikacje klienckie mogą ustawić mapę adresów dla określonej sesji, pobierając Interfejs [IDiaAddressMap](../../debugger/debug-interface-access/idiaaddressmap.md) z interfejsu [IDiaSession](../../debugger/debug-interface-access/idiasession.md) i wywołując metodę [IDiaAddressMap:: set_addressMap](../../debugger/debug-interface-access/idiaaddressmap-set-addressmap.md) , a następnie wywołanie metody [IDiaAddressMap::p ut_addressMapEnabled](../../debugger/debug-interface-access/idiaaddressmap-put-addressmapenabled.md) . `get_addressMapEnabled`Metoda zwraca wyniki wywołania `put_addressMapEnabled` metody.  
  
## <a name="see-also"></a>Zobacz też  
 [IDiaAddressMap](../../debugger/debug-interface-access/idiaaddressmap.md)   
 [IDiaSession](../../debugger/debug-interface-access/idiasession.md)   
 [IDiaAddressMap:: set_addressMap](../../debugger/debug-interface-access/idiaaddressmap-set-addressmap.md)   
 [IDiaAddressMap::put_addressMapEnabled](../../debugger/debug-interface-access/idiaaddressmap-put-addressmapenabled.md)
