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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: a8d544a2172655df91e7156bc3f0d53b236490d1
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "85463674"
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