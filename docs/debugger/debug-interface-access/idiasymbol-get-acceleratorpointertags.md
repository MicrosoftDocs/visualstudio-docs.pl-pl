---
title: 'IDiaSymbol:: get_acceleratorPointerTags | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
ms.assetid: 30e13cee-e511-49ec-affd-99b0097071b2
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: e2da182992999a582ea30f570734b366178a9521
ms.sourcegitcommit: 66f31cc4ce1236e638ab58d2f70d3646206386fa
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/27/2020
ms.locfileid: "85464409"
---
# <a name="idiasymbolget_acceleratorpointertags"></a>IDiaSymbol::get_acceleratorPointerTags
Zwraca wszystkie wartości tagów wskaźnika akceleratora, które odpowiadają funkcji zastępczej akceleratora C++ AMP.

## <a name="syntax"></a>Składnia

```C++
HRESULT get_acceleratorPointerTags(
   DWORD          cnt,
   DWORD*         pcnt,
   DWORD*         pPointerTags);
```

#### <a name="parameters"></a>Parametry
 `cnt`

podczas Rozmiar tablicy wyjściowej `pPointerTags` .

 `pcnt`

określoną Liczba tagów wskaźnika akceleratora w funkcji zastępczej akceleratora C++ AMP.

 `pPointerTags`

określoną `DWORD`Wskaźnik tablicy, który jest wypełniony wartościami tagów wskaźnika akceleratora w funkcji zastępczej akceleratora C++ amp.

## <a name="return-value"></a>Wartość zwracana
 Jeśli powiedzie się, zwraca `S_OK` ; w przeciwnym razie zwraca `S_FALSE` lub kod błędu.

## <a name="remarks"></a>Uwagi
 Ta metoda jest wywoływana w `IDiaSymbol` interfejsie, który odpowiada funkcji zastępczej akceleratora C++ amp.

## <a name="see-also"></a>Zobacz też
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)