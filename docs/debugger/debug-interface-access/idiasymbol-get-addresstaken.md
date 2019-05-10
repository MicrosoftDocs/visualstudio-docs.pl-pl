---
title: Idiasymbol::get_addresstaken — | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
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
ms.openlocfilehash: 468e9865c1648a4bc19f107f7e201d678b672177
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "63402409"
---
# <a name="idiasymbolgetaddresstaken"></a>IDiaSymbol::get_addressTaken
Pobiera flagę wskazującą, czy inny symbol odwołuje się adres tego symbolu.

## <a name="syntax"></a>Składnia

```C++
HRESULT get_addressTaken ( 
   BOOL* pRetVal
);
```

#### <a name="parameters"></a>Parametry
 `pRetVal`

[out] Zwraca `TRUE` Jeśli inny symbol odwołuje się do tego adresu; w przeciwnym razie zwraca `FALSE`.

## <a name="return-value"></a>Wartość zwracana
 Jeśli operacja się powiedzie, zwraca `S_OK`; w przeciwnym razie zwraca `S_FALSE` albo kod błędu.

> [!NOTE]
> Zwracana wartość wynosząca `S_FALSE` oznacza, że właściwość nie jest dostępna dla symbolu.

## <a name="example"></a>Przykład
 W poniższym przykładzie `B` odwołania `A`. W związku z tym, symbol `A`firmy `get_addressTaken` metoda zwraca `TRUE`.

```C++
int A  = 0;
int* B = &A;
```

## <a name="requirements"></a>Wymagania

|Wymaganie|Opis|
|-----------------|-----------------|
|Nagłówek:|dia2.h|
|Wersja:|V7.0 DIA SDK|

## <a name="see-also"></a>Zobacz też
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)