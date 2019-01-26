---
title: Idiasymbol::get_registerid — | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_registerId method
ms.assetid: f881e793-eb9e-48dc-a847-dd61d77174fc
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 7a7007a0d80e1e973bb2c5918cfc5a3194922f8f
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/25/2019
ms.locfileid: "55033469"
---
# <a name="idiasymbolgetregisterid"></a>IDiaSymbol::get_registerId
Pobiera oznaczenie Zarejestruj się w lokalizacji, gdy [locationtype — wyliczenie](../../debugger/debug-interface-access/locationtype.md) ustawiono `LocIsEnregistered`.  
  
## <a name="syntax"></a>Składnia  
  
```C++  
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
>  Zwracana wartość wynosząca `S_FALSE` oznacza, że właściwość nie jest dostępna dla symbolu.  
  
## <a name="remarks"></a>Uwagi  
 Jeśli symbol jest określana względem rejestru, oznacza to, jeśli symbol [locationtype — wyliczenie](../../debugger/debug-interface-access/locationtype.md) jest ustawiona na `LocIsRegRel`, użyj `get_registerId` metody następuje po wywołaniu [idiasymbol::get_offset —](../../debugger/debug-interface-access/idiasymbol-get-offset.md) Metoda pobieranie przesunięcia z rejestru, w którym znajduje się symbol.  
  
## <a name="see-also"></a>Zobacz też  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)   
 [LocationType, wyliczenie](../../debugger/debug-interface-access/locationtype.md)