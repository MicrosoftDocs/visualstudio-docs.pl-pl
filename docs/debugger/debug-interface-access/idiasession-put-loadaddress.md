---
title: IDiaSession::p ut_loadAddress | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSession::put_loadAddress method
ms.assetid: b157b245-1ea0-4b80-8962-d8b278dbc742
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 39db3bc0e0107e734f5de3f6902a2ca0fcc55bb0
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/22/2019
ms.locfileid: "72741889"
---
# <a name="idiasessionput_loadaddress"></a>IDiaSession::put_loadAddress
Ustawia adres ładowania pliku wykonywalnego, który odnosi się do symboli w tym magazynie symboli.

## <a name="syntax"></a>Składnia

```C++
HRESULT put_loadAddress ( 
   ULONGLONG NewVal
);
```

#### <a name="parameters"></a>Parametry
 `NewVal`

podczas Adres ładowania pliku wykonywalnego.

## <a name="remarks"></a>Uwagi
 Właściwości adresu wirtualnego symbolu (VA) są obliczane przy użyciu wartości tej metody. Adresy wirtualne nie są obliczane, chyba że ta właściwość ma wartość różną od zera.

> [!NOTE]
> Należy wywołać tę metodę, gdy zostanie pobrany obiekt [IDiaSession](../../debugger/debug-interface-access/idiasession.md) i przed rozpoczęciem korzystania z obiektu, jeśli konieczne jest użycie dowolnych właściwości wirtualnych w symbolach.

## <a name="see-also"></a>Zobacz także
- [IDiaSession](../../debugger/debug-interface-access/idiasession.md)