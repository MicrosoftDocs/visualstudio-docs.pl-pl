---
title: Idiasymbol::get_packed — | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_packed method
ms.assetid: e42ff368-56c4-49a2-8676-f80e349efa21
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 84cea5ba87c606f66bda1ee09cbf35ae6ef5a643
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/21/2019
ms.locfileid: "56635387"
---
# <a name="idiasymbolgetpacked"></a>IDiaSymbol::get_packed
Pobiera flagę określającą, czy zawiera typ danych zdefiniowany przez użytkownika (UDT).

## <a name="syntax"></a>Składnia

```C++
HRESULT get_packed ( 
   BOOL* pRetVal
);
```

#### <a name="parameters"></a>Parametry
 `pRetVal`

[out] Zwraca `TRUE` Jeśli spakowane UDT; w przeciwnym razie zwraca `FALSE`.

## <a name="return-value"></a>Wartość zwracana
 Jeśli operacja się powiedzie, zwraca `S_OK`; w przeciwnym razie zwraca `S_FALSE` albo kod błędu.

> [!NOTE]
>  Zwracana wartość wynosząca `S_FALSE` oznacza, że właściwość nie jest dostępna dla symbolu.

## <a name="remarks"></a>Uwagi
 Spakowane oznacza, że wszystkie elementy członkowskie typu są umieszczone tak blisko siebie jak to możliwe, za pomocą dopełnienie pośredniczące wyrównywany do granicach pamięci.

## <a name="see-also"></a>Zobacz też
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)