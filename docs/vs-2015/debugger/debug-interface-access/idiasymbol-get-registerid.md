---
title: Idiasymbol::get_registerid — | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_registerId method
ms.assetid: f881e793-eb9e-48dc-a847-dd61d77174fc
caps.latest.revision: 11
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 580637cf1058c8bfbd10ac7812e59c802830d95e
ms.sourcegitcommit: 75807551ea14c5a37aa07dd93a170b02fc67bc8c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/12/2019
ms.locfileid: "64817424"
---
# <a name="idiasymbolgetregisterid"></a>IDiaSymbol::get_registerId
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Pobiera oznaczenie Zarejestruj się w lokalizacji, gdy [locationtype — wyliczenie](../../debugger/debug-interface-access/locationtype.md) ustawiono `LocIsEnregistered`.  
  
## <a name="syntax"></a>Składnia  
  
```cpp#  
HRESULT get_registerId (   
   DWORD* pRetVal  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pRetVal`  
 [out] Zwraca oznaczenie rejestru lokalizacji.  
  
## <a name="return-value"></a>Wartość zwracana  
 Jeśli operacja się powiedzie, zwraca `S_OK`; w przeciwnym razie zwraca `S_FALSE` albo kod błędu.  
  
> [!NOTE]
> Zwracana wartość wynosząca `S_FALSE` oznacza, że właściwość nie jest dostępna dla symbolu.  
  
## <a name="remarks"></a>Uwagi  
 Jeśli symbol jest określana względem rejestru, oznacza to, jeśli symbol [locationtype — wyliczenie](../../debugger/debug-interface-access/locationtype.md) jest ustawiona na `LocIsRegRel`, użyj `get_registerId` metody następuje po wywołaniu [idiasymbol::get_offset —](../../debugger/debug-interface-access/idiasymbol-get-offset.md) Metoda pobieranie przesunięcia z rejestru, w którym znajduje się symbol.  
  
## <a name="see-also"></a>Zobacz też  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)   
 [LocationType, wyliczenie](../../debugger/debug-interface-access/locationtype.md)
