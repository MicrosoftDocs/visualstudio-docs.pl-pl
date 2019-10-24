---
title: 'IDiaSymbol:: get_isAcceleratorStubFunction | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: cc4ea375-76f6-4ba8-baed-c5fa82108137
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: baf71d3be8916c18b16e4022a2af884617b5fd70
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/22/2019
ms.locfileid: "72740305"
---
# <a name="idiasymbolget_isacceleratorstubfunction"></a>IDiaSymbol::get_isAcceleratorStubFunction
Wskazuje, czy symbol odnosi się do symbolu funkcji najwyższego poziomu dla modułu cieniującego skompilowanego dla akceleratora, który odnosi się do wywołania `parallel_for_each`.

## <a name="syntax"></a>Składnia

```C++
HRESULT get_isAcceleratorStubFunction(
   BOOL* pFlag);
```

#### <a name="parameters"></a>Parametry
 `pFlag`

określoną Wskaźnik do `BOOL`, który wskazuje, czy symbol odpowiada symbolowi funkcji najwyższego poziomu dla modułu cieniującego skompilowanego dla akceleratora, który odnosi się do `parallel_for_each` wywołania.

## <a name="return-value"></a>Wartość zwracana
 Jeśli powiedzie się, zwraca `S_OK`; w przeciwnym razie zwraca `S_FALSE` lub kod błędu.

## <a name="see-also"></a>Zobacz także
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)