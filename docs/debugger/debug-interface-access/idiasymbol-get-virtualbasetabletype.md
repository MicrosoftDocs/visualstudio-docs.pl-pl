---
title: 'IDiaSymbol:: get_virtualBaseTableType | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_virtualBaseTableType method
ms.assetid: e0581c4f-0343-49b5-9754-a48477460e9f
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: aaddb8b71ba96511af3682b442c1e5c8e84a409c
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/22/2019
ms.locfileid: "72738840"
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
 Jeśli powiedzie się, zwraca `S_OK`; w przeciwnym razie zwraca `S_FALSE` lub kod błędu.

> [!NOTE]
> Wartość zwracana `S_FALSE` oznacza, że właściwość nie jest dostępna dla symbolu.

## <a name="remarks"></a>Uwagi
 Wskaźnik wirtualnej tabeli podstawowej (`vbtptr`) jest ukrytym wskaźnikiem w [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] tablicy bazowej, która obsługuje dziedziczenie z wirtualnych klas bazowych. @No__t_0 może mieć różne rozmiary w zależności od klas dziedziczonych.

 Ta metoda zwraca obiekt [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md) , którego można użyć do określenia rozmiaru vbtptr.

## <a name="requirements"></a>Wymagania

|Wymaganie|Opis|
|-----------------|-----------------|
|Nagłówki|dia2. h|
|Wersja:|DIA SDK v 8.0|

## <a name="see-also"></a>Zobacz także
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)