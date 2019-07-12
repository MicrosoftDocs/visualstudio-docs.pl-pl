---
title: Idiasymbol::get_virtualbasetabletype — | Dokumentacja firmy Microsoft
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
ms.openlocfilehash: edbd1d8ae66e58611ab538cf0bfe695cb22b3412
ms.sourcegitcommit: 75807551ea14c5a37aa07dd93a170b02fc67bc8c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/12/2019
ms.locfileid: "64793030"
---
# <a name="idiasymbolgetvirtualbasetabletype"></a>IDiaSymbol::get_virtualBaseTableType
Pobiera typ wskaźnika wirtualnego tabeli podstawowej.

## <a name="syntax"></a>Składnia

```C++
HRESULT get_virtualBaseTableType(
   IDiaSymbol *pRetVal
};
```

#### <a name="parameters"></a>Parametry

|Parametr|Opis|
|---------------|-----------------|
|`pRetVal`|[out] Zwraca [idiasymbol —](../../debugger/debug-interface-access/idiasymbol.md) obiektu, który określa typ tabeli podstawowej.|

## <a name="return-value"></a>Wartość zwracana
 Jeśli operacja się powiedzie, zwraca `S_OK`; w przeciwnym razie zwraca `S_FALSE` albo kod błędu.

> [!NOTE]
> Zwracana wartość wynosząca `S_FALSE` oznacza, że właściwość nie jest dostępna dla symbolu.

## <a name="remarks"></a>Uwagi
 Wskaźnik wirtualnego tabeli podstawowej (`vbtptr`) jest ukryty wskaźnik w [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] wartości vtable, która obsługuje dziedziczenie z wirtualnej klasy bazowej. A `vbtptr` mogą mieć różne rozmiary, w zależności od klasy dziedziczone.

 Ta metoda zwraca [idiasymbol —](../../debugger/debug-interface-access/idiasymbol.md) obiekt, który może służyć do określenia rozmiaru vbtptr.

## <a name="requirements"></a>Wymagania

|Wymaganie|Opis|
|-----------------|-----------------|
|Nagłówek:|dia2.h|
|Wersja:|DIA SDK w wersji 8.0|

## <a name="see-also"></a>Zobacz też
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)