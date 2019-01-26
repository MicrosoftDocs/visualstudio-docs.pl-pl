---
title: IDiaSession::findAcceleratorInlineesByLinenum | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: 386c87aa-f7b2-4d38-9dd6-fffba9ff01f0
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 9d963763f341430c92810fe811144212d2cc522e
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/25/2019
ms.locfileid: "54999720"
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