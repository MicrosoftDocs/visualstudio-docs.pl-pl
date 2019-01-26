---
title: IDiaSession::findSymbolsByRVAForAcceleratorPointerTag | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: a073cc45-0c7b-417e-b5fc-a3b08beccdbc
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 49d72f58f57e6779f5f12cc4ed3eba42e6716f63
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/25/2019
ms.locfileid: "54972683"
---
# <a name="idiasessionfindsymbolsbyrvaforacceleratorpointertag"></a>IDiaSession::findSymbolsByRVAForAcceleratorPointerTag
Biorąc pod uwagę odpowiadająca wartość tagu, Metoda ta zwraca wyliczenie symboli, które są zawarte w funkcji klasy zastępczej akceleratora określonego elementu nadrzędnego w określonym względny adres wirtualny.  
  
## <a name="syntax"></a>Składnia  
  
```C++  
HRESULT findSymbolsByRVAForAcceleratorPointerTag (   
   IDiaSymbol*           parent,  
   DWORD                 tagValue,  
   DWORD                 rva,  
   IDiaEnumSymbols**     ppResult  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `parent`  
 [in] `IDiaSymbol` Odnosi się do funkcji klasy zastępczej akcelerator ma być przeszukiwany.  
  
 `tagValue`  
 [in] Wartość tagu wskaźnika.  
  
 `rva`  
 [in] Względny adres wirtualny.  
  
 `ppResult`  
 [out] Wskaźnik do `IDiaEnumSymbols` wskaźnik interfejsu, który jest inicjowany z wynikiem.  
  
## <a name="return-value"></a>Wartość zwracana  
 Jeśli operacja się powiedzie, zwraca `S_OK`; w przeciwnym razie zwraca kod błędu.  
  
## <a name="remarks"></a>Uwagi  
 Tę metodę należy wywołać tylko w systemach `IDiaSymbol` interfejs, który odnosi się do funkcji klasy zastępczej akceleratora.  
  
## <a name="see-also"></a>Zobacz też  
 [Idiasession —](../../debugger/debug-interface-access/idiasession.md)   
 [Idiaenumsymbols —](../../debugger/debug-interface-access/idiaenumsymbols.md)   
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)