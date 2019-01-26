---
title: IDiaSymbol::findInlineeLinesByAddr | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: f1ab47ca-c851-48ea-9c12-47fb80b31102
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 56b2a70ecd0f8d4b7f9e3d49df0e764923f21fac
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/25/2019
ms.locfileid: "54939611"
---
# <a name="idiasymbolfindinlineelinesbyaddr"></a>IDiaSymbol::findInlineeLinesByAddr
Pobiera wyliczenie, które umożliwia klientowi do iterowania po informacje o numerze wiersza wszystkich funkcji, które są śródwierszowych, bezpośrednio lub pośrednio, w tym symbolu w obrębie określonego zakresu adresów.  
  
## <a name="syntax"></a>Składnia  
  
```C++  
HRESULT findInlineeLinesByAddr (   
   DWORD                 isect,  
   DWORD                 offset,  
   DWORD                 length,  
   IDiaEnumLineNumbers** ppResult  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `isect`  
 [in] Określa składnik części adresu.  
  
 `offset`  
 [in] Określa przesunięcie składnik adresu.  
  
 `length`  
 [in] Określa zakres adresów w liczbę bajtów, aby pokrywał się z tym zapytaniem.  
  
 `ppResult`  
 [out] Przechowuje `IDiaEnumLineNumbers` obiektu, który zawiera listę numerów wierszy, które są pobierane.  
  
## <a name="return-value"></a>Wartość zwracana  
 Jeśli operacja się powiedzie, zwraca `S_OK`; w przeciwnym razie zwraca kod błędu.  
  
## <a name="see-also"></a>Zobacz też  
 [Idiasession —](../../debugger/debug-interface-access/idiasession.md)   
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)   
 [Symtagenum — wyliczenie](../../debugger/debug-interface-access/symtagenum.md)   
 [Idiaenumlinenumbers —](../../debugger/debug-interface-access/idiaenumlinenumbers.md)   
 [IDiaSession::findInlineeLines](../../debugger/debug-interface-access/idiasession-findinlineelines.md)