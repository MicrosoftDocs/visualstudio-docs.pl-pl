---
title: 'IDiaSymbol:: get_lexicalParent | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_lexicalParent method
ms.assetid: 4d119965-33a8-474c-9c64-95c5218c389c
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 87d44f2c8dfb723f9f2653d6f9d89a2c1c71ef5f
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/22/2019
ms.locfileid: "72739973"
---
# <a name="idiasymbolget_lexicalparent"></a>IDiaSymbol::get_lexicalParent
Pobiera odwołanie do leksykalnego elementu nadrzędnego symbolu.

## <a name="syntax"></a>Składnia

```C++
HRESULT get_lexicalParent ( 
   IDiaSymbol** pRetVal
);
```

#### <a name="parameters"></a>Parametry
 `pRetVal`

określoną Zwraca obiekt [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md) , który reprezentuje leksykalny element nadrzędny symbolu.

## <a name="return-value"></a>Wartość zwracana
 Jeśli powiedzie się, zwraca `S_OK`; w przeciwnym razie zwraca `S_FALSE` lub kod błędu.

> [!NOTE]
> Wartość zwracana `S_FALSE` oznacza, że właściwość nie jest dostępna dla symbolu.

## <a name="remarks"></a>Uwagi
 Leksykalny element nadrzędny symbolu jest otaczającą funkcję lub moduł. Na przykład leksykalny element nadrzędny parametru funkcji lub zmiennej lokalnej jest sama funkcją, podczas gdy leksykalny element nadrzędny funkcji jest modułem, w którym jest zdefiniowana.

 Możliwe symbole, które mogą występować jako leksykalne rodzice, są udokumentowane w [leksykalnej hierarchii typów symboli](../../debugger/debug-interface-access/lexical-hierarchy-of-symbol-types.md).

## <a name="see-also"></a>Zobacz także
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
- [Hierarchia leksykalna typów symboli](../../debugger/debug-interface-access/lexical-hierarchy-of-symbol-types.md)