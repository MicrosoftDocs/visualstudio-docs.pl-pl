---
description: Pobiera typ wskaźnika wirtualnej tabeli bazowej.
title: 'IDiaSymbol:: get_virtualBaseTableType | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_virtualBaseTableType method
ms.assetid: e0581c4f-0343-49b5-9754-a48477460e9f
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: f67affafd1984f811432a0b69fdcdfec0521e377
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/05/2021
ms.locfileid: "102155517"
---
# <a name="idiasymbolget_virtualbasetabletype"></a>IDiaSymbol::get_virtualBaseTableType
Pobiera typ wskaźnika wirtualnej tabeli bazowej.

## <a name="syntax"></a>Składnia

```C++
HRESULT get_virtualBaseTableType(
   IDiaSymbol *pRetVal
};
```

#### <a name="parameters"></a>Parametry

|Parametr|Opis|
|---------------|-----------------|
|`pRetVal`|określoną Zwraca obiekt [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md) , który określa typ tabeli podstawowej.|

## <a name="return-value"></a>Wartość zwracana
 Jeśli powiedzie się, zwraca `S_OK` ; w przeciwnym razie zwraca `S_FALSE` lub kod błędu.

> [!NOTE]
> Wartość zwracana przez `S_FALSE` oznacza, że właściwość nie jest dostępna dla symbolu.

## <a name="remarks"></a>Uwagi
 Wskaźnik wirtualnej tabeli bazowej ( `vbtptr` ) to ukryty wskaźnik w tablicy [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] metod, który obsługuje dziedziczenie z wirtualnych klas bazowych. `vbtptr`Może mieć różne rozmiary w zależności od klas dziedziczonych.

 Ta metoda zwraca obiekt [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md) , którego można użyć do określenia rozmiaru vbtptr.

## <a name="requirements"></a>Wymagania

|Wymaganie|Opis|
|-----------------|-----------------|
|Nagłówki|dia2. h|
|Wersja:|DIA SDK v 8.0|

## <a name="see-also"></a>Zobacz też
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
