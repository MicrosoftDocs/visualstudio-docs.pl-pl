---
title: 'IDiaSymbol:: get_addressSection | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_addressSection method
ms.assetid: fe80d479-3bb5-4f55-9b62-1bd58d0a60ce
caps.latest.revision: 12
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 85e6ffac13f25e79f51af13ac134cf538e6af5af
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "64782509"
---
# <a name="idiasymbolget_addresssection"></a>IDiaSymbol::get_addressSection
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Pobiera część sekcji lokalizacji adresowej. Użyj, gdy dla [wyliczenia lokalizacji](../../debugger/debug-interface-access/locationtype.md) określono wartość `LocIsStatic` .  
  
## <a name="syntax"></a>Składnia  
  
```cpp#  
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
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)   
 [LocationType, wyliczenie](../../debugger/debug-interface-access/locationtype.md)
