---
title: 'IDiaSession:: get_loadAddress | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSession::get_loadAddress method
ms.assetid: 5162ae1a-38e3-4571-8995-4ed9be1dec3e
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: a971ccb8511d54e934ebe241b3f3285d0b44c321
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99855054"
---
# <a name="idiasessionget_loadaddress"></a>IDiaSession::get_loadAddress
Pobiera adres ładowania pliku wykonywalnego, który odnosi się do symboli w tym magazynie symboli.

## <a name="syntax"></a>Składnia

```C++
HRESULT get_loadAddress ( 
   ULONGLONG* pRetVal
);
```

#### <a name="parameters"></a>Parametry
 `pRetVal`

określoną Zwraca adres wirtualny (VA), w którym jest ładowany plik exe lub plik dll.

## <a name="return-value"></a>Wartość zwracana
 Jeśli powiedzie się, zwraca `S_OK` ; w przeciwnym razie zwraca kod błędu.

## <a name="remarks"></a>Uwagi
 Zwrócony adres ładowania jest zawsze zerem, chyba że jest to określone przy użyciu metody [IDiaSession::p ut_loadAddress](../../debugger/debug-interface-access/idiasession-put-loadaddress.md) .

## <a name="see-also"></a>Zobacz też
- [IDiaSession](../../debugger/debug-interface-access/idiasession.md)
- [IDiaSession::put_loadAddress](../../debugger/debug-interface-access/idiasession-put-loadaddress.md)