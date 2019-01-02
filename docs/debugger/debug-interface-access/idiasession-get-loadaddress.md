---
title: Idiasession::get_loadaddress — | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSession::get_loadAddress method
ms.assetid: 5162ae1a-38e3-4571-8995-4ed9be1dec3e
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: bd52a6cba05c4757eaefcc1518d4e659c4c89643
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/02/2019
ms.locfileid: "53951264"
---
# <a name="idiasessiongetloadaddress"></a>IDiaSession::get_loadAddress
Pobiera adres obciążenia dla pliku wykonywalnego, który odnosi się do symboli w tym magazynie symboli.  
  
## <a name="syntax"></a>Składnia  
  
```C++  
HRESULT get_loadAddress (   
   ULONGLONG* pRetVal  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pRetVal`  
 [out] Zwraca adresów wirtualnych (oceny luk w zabezpieczeniach), gdzie jest ładowany pliku .exe lub .dll.  
  
## <a name="return-value"></a>Wartość zwracana  
 Jeśli operacja się powiedzie, zwraca `S_OK`; w przeciwnym razie zwraca kod błędu.  
  
## <a name="remarks"></a>Uwagi  
 Adres zwrócone obciążenia zawsze wynosi zero, chyba że specjalnie można ustawić przy użyciu [idiasession::put_loadaddress —](../../debugger/debug-interface-access/idiasession-put-loadaddress.md) metody.  
  
## <a name="see-also"></a>Zobacz też  
 [Idiasession —](../../debugger/debug-interface-access/idiasession.md)   
 [IDiaSession::put_loadAddress](../../debugger/debug-interface-access/idiasession-put-loadaddress.md)