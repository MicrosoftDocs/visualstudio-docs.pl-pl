---
title: 'IDiaSymbol:: get_isAcceleratorStubFunction | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
ms.assetid: cc4ea375-76f6-4ba8-baed-c5fa82108137
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: dcc8128ec5c9693b399c08a134326b1f6d135d1b
ms.sourcegitcommit: 66f31cc4ce1236e638ab58d2f70d3646206386fa
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/27/2020
ms.locfileid: "85463492"
---
# <a name="idiasymbolget_isacceleratorstubfunction"></a>IDiaSymbol::get_isAcceleratorStubFunction
Wskazuje, czy symbol odnosi się do symbolu funkcji najwyższego poziomu dla modułu cieniującego skompilowanego dla akceleratora, który odnosi się do `parallel_for_each` wywołania.

## <a name="syntax"></a>Składnia

```C++
HRESULT get_isAcceleratorStubFunction(
   BOOL* pFlag);
```

#### <a name="parameters"></a>Parametry
 `pFlag`

określoną Wskaźnik do obiektu `BOOL` , który wskazuje, czy symbol odpowiada symbolowi funkcji najwyższego poziomu dla modułu cieniującego skompilowanego dla akceleratora, który odpowiada `parallel_for_each` wywołaniu.

## <a name="return-value"></a>Wartość zwracana
 Jeśli powiedzie się, zwraca `S_OK` ; w przeciwnym razie zwraca `S_FALSE` lub kod błędu.

## <a name="see-also"></a>Zobacz też
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)