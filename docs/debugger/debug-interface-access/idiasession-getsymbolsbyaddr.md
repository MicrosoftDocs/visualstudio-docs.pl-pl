---
title: 'IDiaSession:: getSymbolsByAddr | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSession::getSymbolsByAddr method
ms.assetid: eafcc757-b488-487d-a063-ad3703ff42e8
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 241f2860a6ed3b1bc57fb8e2d959ad5b26decc68
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99864090"
---
# <a name="idiasessiongetsymbolsbyaddr"></a>IDiaSession::getSymbolsByAddr
Pobiera moduł wyliczający, który odnajdzie symbole w kolejności ich adresów.

## <a name="syntax"></a>Składnia

```C++
HRESULT getSymbolsByAddr( 
   IDiaEnumSymbolsByAddr** ppEnumbyAddr
);
```

#### <a name="parameters"></a>Parametry
 `ppEnumbyAddr`

określoną Zwraca obiekt [IDiaEnumSymbolsByAddr](../../debugger/debug-interface-access/idiaenumsymbolsbyaddr.md) . Użyj tego interfejsu do wyszukiwania symboli w magazynie symboli według lokalizacji pamięci.

## <a name="return-value"></a>Wartość zwracana
 Jeśli powiedzie się, zwraca `S_OK` ; w przeciwnym razie zwraca kod błędu.

## <a name="see-also"></a>Zobacz też
- [IDiaSession](../../debugger/debug-interface-access/idiasession.md)
- [IDiaEnumSymbolsByAddr](../../debugger/debug-interface-access/idiaenumsymbolsbyaddr.md)