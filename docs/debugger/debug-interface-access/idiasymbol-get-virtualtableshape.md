---
title: 'IDiaSymbol:: get_virtualTableShape | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_virtualTableShape method
ms.assetid: 92360cbd-0761-446e-93f9-04dc8f4b66c6
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 62eb3879fd30bfd4820dd0f53b864140127f51a9
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99853374"
---
# <a name="idiasymbolget_virtualtableshape"></a>IDiaSymbol::get_virtualTableShape
Pobiera interfejs symbol typu tabeli wirtualnej dla typu zdefiniowanego przez użytkownika.

## <a name="syntax"></a>Składnia

```C++
HRESULT get_virtualTableShape ( 
   IDiaSymbol** pRetVal
);
```

#### <a name="parameters"></a>Parametry
 `pRetVal`

określoną Zwraca obiekt [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md) reprezentujący tabelę wirtualną dla typu zdefiniowanego przez użytkownika.

## <a name="return-value"></a>Wartość zwracana
 Jeśli powiedzie się, zwraca `S_OK` ; w przeciwnym razie zwraca `S_FALSE` lub kod błędu.

> [!NOTE]
> Wartość zwracana przez `S_FALSE` oznacza, że właściwość nie jest dostępna dla symbolu.

## <a name="see-also"></a>Zobacz też
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)