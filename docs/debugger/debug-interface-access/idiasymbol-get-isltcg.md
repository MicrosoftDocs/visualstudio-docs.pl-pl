---
description: Pobiera flagę, która określa, czy jednostka kompilacji) zostało połączone z przełącznikiem konsolidatora/LTCG (generowanie kodu w czasie konsolidacji) (/CPP/Build/Reference/LTCG-link-Time-Code-Generation), które ułatwia optymalizację w całym programie.
title: 'IDiaSymbol:: get_isLTCG | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_isLTCG method
ms.assetid: 5f7f05b8-6b71-4958-9e1e-e4924ef9c59b
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 1b8306dabe6533287d7d28841ea76f2d6478e4a3
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/05/2021
ms.locfileid: "102160814"
---
# <a name="idiasymbolget_isltcg"></a>IDiaSymbol::get_isLTCG
Pobiera flagę, która określa, czy [jednostka kompilacji](../../debugger/debug-interface-access/compiland.md) jest połączona z przełącznikiem konsolidatora [/LTCG (generowanie kodu w czasie konsolidacji)](/cpp/build/reference/ltcg-link-time-code-generation), które ułatwia optymalizację w całym programie. Ten przełącznik ma zastosowanie tylko do kodu zarządzanego.

## <a name="syntax"></a>Składnia

```C++
HRESULT get_iSLTCG(
   BOOL *pFlag
);
```

#### <a name="parameters"></a>Parametry
 pFlag

określoną Zwraca `TRUE` czy `compiland` został połączony z przełącznikiem konsolidatora/LTCG; w przeciwnym razie zwraca `FALSE` .

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
