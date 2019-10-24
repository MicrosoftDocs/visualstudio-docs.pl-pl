---
title: 'IDiaSymbol:: get_numberOfAcceleratorPointerTags | Microsoft Docs'
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
ms.openlocfilehash: 47c5827348c7b7cb450017a0e6176d71f555c841
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/22/2019
ms.locfileid: "72739699"
---
# <a name="idiasymbolget_numberofacceleratorpointertags"></a>IDiaSymbol::get_numberOfAcceleratorPointerTags
Zwraca liczbę tagów wskaźnika akceleratora w funkcji zastępczej C++ amp.

## <a name="syntax"></a>Składnia

```C++
HRESULT get_numberOfAcceleratorPointerTags(
   DWORD* count);
```

#### <a name="parameters"></a>Parametry
 `count`

określoną Wskaźnik do `DWORD`, który przechowuje liczbę tagów wskaźnika akceleratora w funkcji zastępczej C++ amp.

## <a name="return-value"></a>Wartość zwracana
 Jeśli powiedzie się, zwraca `S_OK`; w przeciwnym razie zwraca `S_FALSE` lub kod błędu.

## <a name="remarks"></a>Uwagi
 Ta metoda jest wywoływana w interfejsie `IDiaSymbol`, który odpowiada funkcji zastępczej akceleratora C++ amp.

## <a name="see-also"></a>Zobacz także
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)