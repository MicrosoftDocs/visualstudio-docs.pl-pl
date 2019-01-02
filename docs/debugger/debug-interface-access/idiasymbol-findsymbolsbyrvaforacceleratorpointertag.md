---
title: IDiaSymbol::findSymbolsByRVAForAcceleratorPointerTag | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: 024ccd78-5867-4ca7-bc26-548758e9ac53
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 0c084bf3bb9b28a6af0ddc1aa53c0707d8876966
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/02/2019
ms.locfileid: "53827981"
---
# <a name="idiasymbolfindsymbolsbyrvaforacceleratorpointertag"></a>IDiaSymbol::findSymbolsByRVAForAcceleratorPointerTag
Biorąc pod uwagę odpowiadająca wartość tagu, Metoda ta zwraca wyliczenie symboli, które są zawarte w tej funkcji klasy zastępczej w określonym względny adres wirtualny.  
  
## <a name="syntax"></a>Składnia  
  
```C++  
HRESULT findSymbolsByRVAForAcceleratorPointerTag (   
   DWORD             tagValue,  
   DWORD             rva,  
   IDiaEnumSymbols** ppResult);  
```  
  
#### <a name="parameters"></a>Parametry  
 `tagValue`  
 [in] Wartość tagu wskaźnika, dla której rekordy symbol pointee zostaną znalezione.  
  
 `rva`  
 [in] Adres rva, która jest używana do filtrowania symboli, które odnoszą się do zmiennej pointee wartością określonego tagu.  
  
 `ppResult`  
 [out] Wskaźnik do `IDiaEnumSymbols` wskaźnika interfejsu, który jest inicjowany z wynikiem.  
  
## <a name="return-value"></a>Wartość zwracana  
 Jeśli operacja się powiedzie, zwraca `S_OK`; w przeciwnym razie zwraca `S_FALSE` albo kod błędu.  
  
## <a name="remarks"></a>Uwagi  
 Tę metodę należy wywołać tylko w systemach `IDiaSymbol` interfejs, który odnosi się do funkcji klasy zastępczej akceleratora.  
  
## <a name="see-also"></a>Zobacz też  
 [Idiasymbol —](../../debugger/debug-interface-access/idiasymbol.md)   
 [IDiaEnumSymbols](../../debugger/debug-interface-access/idiaenumsymbols.md)