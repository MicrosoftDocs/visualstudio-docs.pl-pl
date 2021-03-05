---
description: Wskazuje, czy symbol odnosi się do symbolu funkcji najwyższego poziomu dla modułu cieniującego skompilowanego dla akceleratora, który odnosi się do wywołania parallel_for_each.
title: 'IDiaSymbol:: get_isAcceleratorStubFunction | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
ms.assetid: cc4ea375-76f6-4ba8-baed-c5fa82108137
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 710622fdb8fb10d0357c060097f13bab3be7d05f
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/05/2021
ms.locfileid: "102156217"
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
