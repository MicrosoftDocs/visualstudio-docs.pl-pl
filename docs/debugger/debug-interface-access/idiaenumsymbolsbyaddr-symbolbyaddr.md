---
title: 'IDiaEnumSymbolsByAddr:: symbolByAddr | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
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
ms.openlocfilehash: b0891cc5eb244b781b69e231d4282b92aa064b91
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/22/2019
ms.locfileid: "72743846"
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
 Jeśli powiedzie się, zwraca `S_OK`. Zwraca `S_FALSE`, jeśli nie można znaleźć symbolu. W przeciwnym razie zwraca kod błędu.

## <a name="see-also"></a>Zobacz także
- [IDiaEnumSymbolsByAddr](../../debugger/debug-interface-access/idiaenumsymbolsbyaddr.md)
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)