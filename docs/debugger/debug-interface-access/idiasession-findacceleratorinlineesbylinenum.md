---
title: IDiaSession::findAcceleratorInlineesByLinenum | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: 386c87aa-f7b2-4d38-9dd6-fffba9ff01f0
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: e6784808075518db2e5dcb660318d8e6631cb1b7
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/02/2019
ms.locfileid: "53867816"
---
# <a name="idiasessionfindacceleratorinlineesbylinenum"></a>IDiaSession::findAcceleratorInlineesByLinenum
Zwraca wyliczenie symboli dla ramek wbudowanych, które odnoszą się do określonej lokalizacji źródłowej.  
  
## <a name="syntax"></a>Składnia  
  
```C++  
HRESULT findAcceleratorInlineeLinesByName (   
   IDiaSymbol*           parent,  
   IDiaSourceFile*       file,  
   DWORD                 linenum,  
   DWORD                 colnum,  
   IDiaEnumLineNumbers** ppResult  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `parent`  
 [in] `IDiaSymbol` Odnosi się do funkcji klasy zastępczej akceleratora, która ma być przeszukiwany.  
  
 `file`  
 [in] `IDiaSourceFile` Lokalizacji źródła.  
  
 `linenum`  
 [in] Numer wiersza lokalizacji źródła.  
  
 `colnum`  
 [in] Numer kolumny lokalizacji źródła.  
  
 `ppResult`  
 [out] Wskaźnik do `IDiaEnumLineNumbers` wskaźnik interfejsu, który jest inicjowany z wynikiem.  
  
## <a name="return-value"></a>Wartość zwracana  
 Jeśli operacja się powiedzie, zwraca `S_OK`; w przeciwnym razie zwraca kod błędu.  
  
## <a name="see-also"></a>Zobacz też  
 [Idiasession —](../../debugger/debug-interface-access/idiasession.md)   
 [Idiaenumlinenumbers —](../../debugger/debug-interface-access/idiaenumlinenumbers.md)   
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)