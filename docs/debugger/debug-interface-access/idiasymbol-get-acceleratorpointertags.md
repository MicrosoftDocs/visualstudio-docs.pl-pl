---
title: 'IDiaSymbol:: get_acceleratorPointerTags | Microsoft Docs'
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
ms.openlocfilehash: f36b4bf9fdd362f4941e33745d59d481a473c607
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/22/2019
ms.locfileid: "72741114"
---
# <a name="idiasymbolget_acceleratorpointertags"></a>IDiaSymbol::get_acceleratorPointerTags
Zwraca wszystkie wartości tagów wskaźnika akceleratora, które odpowiadają funkcji zastępczej akceleratora C++ amp.

## <a name="syntax"></a>Składnia

```C++
HRESULT get_acceleratorPointerTags(
   DWORD          cnt,
   DWORD*         pcnt,
   DWORD*         pPointerTags);
```

#### <a name="parameters"></a>Parametry
 `cnt`

podczas Rozmiar tablicy wyjściowej `pPointerTags`.

 `pcnt`

określoną Liczba tagów wskaźnika akceleratora w funkcji zastępczej akceleratora C++ amp.

 `pPointerTags`

określoną @No__t_0 wskaźnik tablicy, który jest wypełniony wartościami tagów wskaźnika akceleratora w funkcji zastępczej akceleratora C++ amp.

## <a name="return-value"></a>Wartość zwracana
 Jeśli powiedzie się, zwraca `S_OK`; w przeciwnym razie zwraca `S_FALSE` lub kod błędu.

## <a name="remarks"></a>Uwagi
 Ta metoda jest wywoływana w interfejsie `IDiaSymbol`, który odpowiada funkcji zastępczej akceleratora C++ amp.

## <a name="see-also"></a>Zobacz także
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)