---
title: IDiaSymbol::get_acceleratorPointerTags | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: 30e13cee-e511-49ec-affd-99b0097071b2
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: c1724ee3e81ac00ed048f323105842361ec22bc7
ms.sourcegitcommit: 75807551ea14c5a37aa07dd93a170b02fc67bc8c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/12/2019
ms.locfileid: "62827297"
---
# <a name="idiasymbolgetacceleratorpointertags"></a>IDiaSymbol::get_acceleratorPointerTags
Zwraca wszystkie akceleratora wskaźnik wartości tagów, które odpowiadają do funkcji klasy zastępczej akceleratora C++ AMP.

## <a name="syntax"></a>Składnia

```C++
HRESULT get_acceleratorPointerTags(
   DWORD          cnt,
   DWORD*         pcnt,
   DWORD*         pPointerTags);
```

#### <a name="parameters"></a>Parametry
 `cnt`

[in] Rozmiar tablicy danych wyjściowych `pPointerTags`.

 `pcnt`

[out] Liczba tagów wskaźnika akceleratora w C++ funkcji klasy zastępczej akcelerator AMP.

 `pPointerTags`

[out] A `DWORD` wskaźnika tablicy, który zostanie wypełniony kolorem wartości tagów wskaźnika akceleratora w C++ funkcji klasy zastępczej akcelerator AMP.

## <a name="return-value"></a>Wartość zwracana
 Jeśli operacja się powiedzie, zwraca `S_OK`; w przeciwnym razie zwraca `S_FALSE` albo kod błędu.

## <a name="remarks"></a>Uwagi
 Ta metoda jest wywoływana w `IDiaSymbol` interfejs, który odnosi się do funkcji klasy zastępczej akceleratora C++ AMP.

## <a name="see-also"></a>Zobacz też
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)