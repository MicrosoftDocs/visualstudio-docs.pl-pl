---
title: Idiasymbol::get_rank — | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_rank method
ms.assetid: 14cc9c4b-a5ec-414a-b01f-4a142c17b7cc
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 646672904aebb8e4c0fcdd5200b60c2a2349a859
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/21/2019
ms.locfileid: "56639287"
---
# <a name="idiasymbolgetrank"></a>IDiaSymbol::get_rank
Pobiera rangę tablicy wielowymiarowej FORTRAN (liczba wymiarów).

## <a name="syntax"></a>Składnia

```C++
HRESULT get_rank ( 
   DWORD* pRetVal
);
```

#### <a name="parameters"></a>Parametry
 `pRetVal`

[out] Zwraca liczbę wymiarów w tablicy wielowymiarowej FORTRAN.

## <a name="return-value"></a>Wartość zwracana
 Jeśli operacja się powiedzie, zwraca `S_OK`; w przeciwnym razie zwraca `S_FALSE` albo kod błędu.

> [!NOTE]
>  Zwracana wartość wynosząca `S_FALSE` oznacza, że właściwość nie jest dostępna dla symbolu.

## <a name="remarks"></a>Uwagi
 Ranga odnosi się do liczby wymiarów w tablicy, gdy tablica jest zadeklarowana jako `myarray[1,2,3]`. W tym przykładzie randze wymiary 3 i 3. Ranga nie ma zastosowania do języka C++, która korzysta z koncepcji tablicy tablic dla każdego wymiaru (czyli `myarray[1][2][3]`).

## <a name="see-also"></a>Zobacz też
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)