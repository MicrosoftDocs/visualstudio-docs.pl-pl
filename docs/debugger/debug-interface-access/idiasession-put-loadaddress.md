---
title: IDiaSession::p ut_loadAddress | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
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
ms.openlocfilehash: 807346ef5a34c0b175257fe2099dc25e8de692f6
ms.sourcegitcommit: 66f31cc4ce1236e638ab58d2f70d3646206386fa
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/27/2020
ms.locfileid: "85465385"
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

## <a name="see-also"></a>Zobacz też
- [IDiaSession](../../debugger/debug-interface-access/idiasession.md)