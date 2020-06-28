---
title: 'IDiaSymbol:: get_addressTaken | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_addressTaken method
ms.assetid: 0d366188-f5e1-4226-b392-58c09539d097
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 6b62a848d70b59a1764220c806123b0edd03edf2
ms.sourcegitcommit: 66f31cc4ce1236e638ab58d2f70d3646206386fa
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/27/2020
ms.locfileid: "85464353"
---
# <a name="idiasymbolget_addresstaken"></a>IDiaSymbol::get_addressTaken
Pobiera flagę wskazującą, czy inny symbol odwołuje się do adresu tego symbolu.

## <a name="syntax"></a>Składnia

```C++
HRESULT get_addressTaken ( 
   BOOL* pRetVal
);
```

#### <a name="parameters"></a>Parametry
 `pRetVal`

określoną Zwraca `TRUE` czy inny symbol odwołuje się do tego adresu; w przeciwnym razie zwraca `FALSE` .

## <a name="return-value"></a>Wartość zwracana
 Jeśli powiedzie się, zwraca `S_OK` ; w przeciwnym razie zwraca `S_FALSE` lub kod błędu.

> [!NOTE]
> Wartość zwracana przez `S_FALSE` oznacza, że właściwość nie jest dostępna dla symbolu.

## <a name="example"></a>Przykład
 W poniższym przykładzie `B` odwołania `A` . W związku z tym, `A` `get_addressTaken` Metoda symbol zwraca wartość `TRUE` .

```C++
int A  = 0;
int* B = &A;
```

## <a name="requirements"></a>Wymagania

|Wymaganie|Opis|
|-----------------|-----------------|
|Nagłówki|dia2. h|
|Wersja:|DIA SDK v 7.0|

## <a name="see-also"></a>Zobacz też
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)