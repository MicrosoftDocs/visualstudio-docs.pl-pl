---
title: 'IDiaEnumSymbolsByAddr:: symbolByAddr | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumSymbolsByAddr::symbolByAddr method
ms.assetid: 0b6f5a68-8402-4f29-8219-20576fda8166
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 9750c57bc9a6cacc8d945b0acdd7723769e74e53
ms.sourcegitcommit: 66f31cc4ce1236e638ab58d2f70d3646206386fa
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/27/2020
ms.locfileid: "85467632"
---
# <a name="idiaenumsymbolsbyaddrsymbolbyaddr"></a>IDiaEnumSymbolsByAddr::symbolByAddr
Umieszcza moduł wyliczający, wykonując wyszukiwanie według numeru sekcji obrazu i przesunięcia.

## <a name="syntax"></a>Składnia

```C++
HRESULT symbolByAddr ( 
   DWORD**      isect,
   DWORD**      offsect,
   IDiaSymbol** ppsymbol
);
```

#### <a name="parameters"></a>Parametry
 isect

podczas Numer sekcji obrazu.

 offsect

podczas Przesunięcie w sekcji.

 ppsymbol

określoną Zwraca obiekt [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md) reprezentujący znaleziony symbol.

## <a name="return-value"></a>Wartość zwracana
 Jeśli powiedzie się, zwraca `S_OK` . Zwraca `S_FALSE` czy nie można znaleźć symbolu. W przeciwnym razie zwraca kod błędu.

## <a name="see-also"></a>Zobacz też
- [IDiaEnumSymbolsByAddr](../../debugger/debug-interface-access/idiaenumsymbolsbyaddr.md)
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)