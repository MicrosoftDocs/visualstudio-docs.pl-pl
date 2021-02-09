---
title: 'IDiaSymbol:: get_hasSecurityChecks | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_hasSecurityChecks method
ms.assetid: 4bb51f62-8645-41a4-bc44-1451010623fd
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 03e4415b57e687aefc5e165ffef85302c3610644
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99854228"
---
# <a name="idiasymbolget_hassecuritychecks"></a>IDiaSymbol::get_hasSecurityChecks
Pobiera flagę, która określa, czy jednostka kompilacji lub funkcja została skompilowana przy użyciu kontroli zabezpieczeń przepełnienia buforu (na przykład przełącznika kompilatora [/GS (sprawdzanie zabezpieczeń bufora)](/cpp/build/reference/gs-buffer-security-check) .

## <a name="syntax"></a>Składnia

```C++
HRESULT get_hasSecurityChecks(
   BOOL *pFlag
);
```

#### <a name="parameters"></a>Parametry
 `pFlag`

określoną Zwraca `TRUE` czy funkcja ma jakiekolwiek sprawdzenia zabezpieczeń; w przeciwnym razie zwraca wartość `FALSE` .

## <a name="return-value"></a>Wartość zwracana
 Jeśli powiedzie się, zwraca `S_OK` ; w przeciwnym razie zwraca `S_FALSE` lub kod błędu.

> [!NOTE]
> Wartość zwracana przez `S_FALSE` oznacza, że właściwość nie jest dostępna dla symbolu.

## <a name="requirements"></a>Wymagania

|Wymaganie|Opis|
|-----------------|-----------------|
|Nagłówki|dia2. h|
|Wersja:|DIA SDK v 8.0|

## <a name="see-also"></a>Zobacz też
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
- [/GS (sprawdzanie zabezpieczeń bufora)](/cpp/build/reference/gs-buffer-security-check)