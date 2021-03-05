---
description: Pobiera flagę wskazującą, czy moduł został skompilowany przy użyciu przełącznika kompilatora/Z7,/Zi,/ZI (Debug Information Format)).
title: 'IDiaSymbol:: get_editAndContinueEnabled | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_editAndContinueEnabled method
ms.assetid: cd703c64-9ff8-4654-8493-8cde9309cb22
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: ead107b051dd898b549ee25f800a8b8d2e83973a
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/05/2021
ms.locfileid: "102156350"
---
# <a name="idiasymbolget_editandcontinueenabled"></a>IDiaSymbol::get_editAndContinueEnabled
Pobiera flagę wskazującą, czy moduł został skompilowany przy użyciu przełącznika kompilatora [/Z7,/Zi,/ZI (Debug Information Format)](/cpp/build/reference/z7-zi-zi-debug-information-format) .

## <a name="syntax"></a>Składnia

```C++
HRESULT get_editAndContinueEnabled ( 
   BOOL* pRetVal
);
```

#### <a name="parameters"></a>Parametry
 `pRetVal`

określoną Zwraca `TRUE` czy funkcja Edit-and-Continue została włączona podczas kompilacji; w przeciwnym razie zwraca wartość `FALSE` .

## <a name="return-value"></a>Wartość zwracana
 Jeśli powiedzie się, zwraca `S_OK` ; w przeciwnym razie zwraca `S_FALSE` lub kod błędu.

> [!NOTE]
> Wartość zwracana przez `S_FALSE` oznacza, że właściwość nie jest dostępna dla symbolu.

## <a name="requirements"></a>Wymagania

|Wymaganie|Opis|
|-----------------|-----------------|
|Nagłówki|dia2. h|
|Wersja:|DIA SDK v 7.0|

## <a name="see-also"></a>Zobacz też
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
- [/Z7,/Zi,/ZI (format informacji o debugowaniu)](/cpp/build/reference/z7-zi-zi-debug-information-format)
