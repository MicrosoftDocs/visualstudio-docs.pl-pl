---
title: Idiasymbol::get_volatiletype — | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_volatileType method
ms.assetid: 19782a4d-40a8-467b-ab7d-58bc4d812309
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: cef843a2e214dbf66107a5ac7462ae6a2672fafe
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "63400590"
---
# <a name="idiasymbolgetvolatiletype"></a>IDiaSymbol::get_volatileType
Pobiera flagę określającą, czy typ danych zdefiniowany przez użytkownika (UDT) jest nietrwały.

## <a name="syntax"></a>Składnia

```C++
HRESULT get_volatileType ( 
   BOOL* pRetVal
);
```

#### <a name="parameters"></a>Parametry
 `pRetVal`

[out] Zwraca `TRUE` w przypadku UDT volatile; w przeciwnym razie, zwraca `FALSE`.

## <a name="return-value"></a>Wartość zwracana
 Jeśli operacja się powiedzie, zwraca `S_OK`; w przeciwnym razie zwraca `S_FALSE` albo kod błędu.

> [!NOTE]
> Zwracana wartość wynosząca `S_FALSE` oznacza, że właściwość nie jest dostępna dla symbolu.

## <a name="remarks"></a>Uwagi
 W języku C++, mogą być oznaczone UDT `volatile` — słowo kluczowe, wskazujący, że jego zawartość nie zakłada się, że istnieje jeden dostępem do następnego.

## <a name="see-also"></a>Zobacz też
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)