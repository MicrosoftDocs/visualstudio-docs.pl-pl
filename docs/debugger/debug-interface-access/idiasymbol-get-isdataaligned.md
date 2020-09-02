---
title: 'IDiaSymbol:: get_isDataAligned | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_isDataAligned method
ms.assetid: ddd11a41-6c00-4829-acf4-aa1ace8c21a7
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 00507b5d69f46657968407170d9633f1d84c8e4f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "85463429"
---
# <a name="idiasymbolget_isdataaligned"></a>IDiaSymbol::get_isDataAligned
Pobiera flagę, która określa, czy typ zdefiniowany przez użytkownika (UDT) został wyrównany do określonej granicy pamięci.

## <a name="syntax"></a>Składnia

```C++
HRESULT get_isDataAligned(
   BOOL *pFlag
);
```

#### <a name="parameters"></a>Parametry
 `pFlag`

określoną Zwraca `TRUE` czy typ UDT został wyrównany do pewnej granicy pamięci; w przeciwnym razie zwraca `FALSE` .

## <a name="return-value"></a>Wartość zwracana
 Jeśli powiedzie się, zwraca `S_OK` ; w przeciwnym razie zwraca `S_FALSE` lub kod błędu.

> [!NOTE]
> Wartość zwracana przez `S_FALSE` oznacza, że właściwość nie jest dostępna dla symbolu.

## <a name="remarks"></a>Uwagi
 Ta właściwość jest zazwyczaj ustawiana, gdy plik wykonywalny jest kompilowany z niedomyślnymi wyrównaniami danych. Na przykład kompilator języka Microsoft C++ może zmienić wyrównanie danych za pomocą opcji wiersza polecenia/ZP <em>#</em> , gdzie *#* jest wartością typu Byte.

## <a name="requirements"></a>Wymagania

|Wymaganie|Opis|
|-----------------|-----------------|
|Nagłówki|dia2. h|
|Wersja:|DIA SDK v 8.0|

## <a name="see-also"></a>Zobacz też
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)