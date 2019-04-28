---
title: IDiaSymbol::get_numberOfAcceleratorPointerTags | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: 1886e3ec-b227-4187-8d93-c5144b4b77ae
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 283533b20614ea727be620669ea5ab66cf00e5ed
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62835777"
---
# <a name="idiasymbolgetnumberofacceleratorpointertags"></a>IDiaSymbol::get_numberOfAcceleratorPointerTags
Zwraca liczbę znaczników wskaźnika akceleratora w funkcji skrótową, C++ AMP.

## <a name="syntax"></a>Składnia

```C++
HRESULT get_numberOfAcceleratorPointerTags(
   DWORD* count);
```

#### <a name="parameters"></a>Parametry
 `count`

[out] Wskaźnik do `DWORD` przechowuje liczbę akceleratora tagów wskaźnika w C++ funkcji klasy zastępczej AMP.

## <a name="return-value"></a>Wartość zwracana
 Jeśli operacja się powiedzie, zwraca `S_OK`; w przeciwnym razie zwraca `S_FALSE` albo kod błędu.

## <a name="remarks"></a>Uwagi
 Ta metoda jest wywoływana w `IDiaSymbol` interfejs, który odnosi się do funkcji klasy zastępczej akceleratora C++ AMP.

## <a name="see-also"></a>Zobacz też
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)