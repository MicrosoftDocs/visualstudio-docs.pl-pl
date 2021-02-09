---
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
ms.openlocfilehash: 0dc951b069342478301b0cf815d1c226f9f1da11
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99854137"
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