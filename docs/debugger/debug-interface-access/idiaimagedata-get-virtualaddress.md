---
title: Idiaimagedata::get_virtualaddress — | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaImageData::get_virtualAddress method
ms.assetid: 67ecdc8c-d342-4d0b-b02a-c6b88e22fd02
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: c5df2098c4859205ef07648c214f43b74e53673d
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/21/2019
ms.locfileid: "56638572"
---
# <a name="idiaimagedatagetvirtualaddress"></a>IDiaImageData::get_virtualAddress
Pobiera lokalizację w pamięci wirtualnej obrazu.

## <a name="syntax"></a>Składnia

```C++
HRESULT get_virtualAddress ( 
   ULONGLONG* pRetVal
);
```

#### <a name="parameters"></a>Parametry
 `pRetVal`

[out] Zwraca adres wirtualny obrazu.

## <a name="return-value"></a>Wartość zwracana
 Jeśli operacja się powiedzie, zwraca `S_OK`; w przeciwnym razie zwraca kod błędu.

## <a name="see-also"></a>Zobacz też
- [IDiaImageData](../../debugger/debug-interface-access/idiaimagedata.md)