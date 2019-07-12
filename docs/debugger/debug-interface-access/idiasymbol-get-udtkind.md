---
title: Idiasymbol::get_udtkind — | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_udtKind method
ms.assetid: 4002f887-aea6-4475-b302-67c57079fe0a
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 34faf217f77bd30ba707f5ae17886b05dac8ab4f
ms.sourcegitcommit: 75807551ea14c5a37aa07dd93a170b02fc67bc8c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/12/2019
ms.locfileid: "64796641"
---
# <a name="idiasymbolgetudtkind"></a>IDiaSymbol::get_udtKind
Pobiera różne typu zdefiniowanego przez użytkownika (UDT).

## <a name="syntax"></a>Składnia

```C++
HRESULT get_udtKind ( 
   DWORD* pRetVal
);
```

#### <a name="parameters"></a>Parametry
 `pRetVal`

[out] Zwraca wartość z zakresu od [udtkind — wyliczenie](../../debugger/debug-interface-access/udtkind.md) wyliczenie, które określa rodzaj UDT: struktury, klasy lub Unii.

## <a name="return-value"></a>Wartość zwracana
 Jeśli operacja się powiedzie, zwraca `S_OK`; w przeciwnym razie zwraca `S_FALSE` lub kod błędu.

> [!NOTE]
> Zwracana wartość wynosząca `S_FALSE` oznacza, że właściwość nie jest dostępna dla symbolu.

## <a name="see-also"></a>Zobacz też
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
- [UdtKind, wyliczenie](../../debugger/debug-interface-access/udtkind.md)