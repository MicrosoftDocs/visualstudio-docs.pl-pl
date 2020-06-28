---
title: 'IDiaEnumSymbolsByAddr:: symbolByRVA | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumSymbolsByAddr::symbolByRVA method
ms.assetid: f7828029-f2ee-4ccd-afac-785adc60a4c8
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: eb6f2f4486f943064ef4c29d16c98003aa3ff088
ms.sourcegitcommit: 66f31cc4ce1236e638ab58d2f70d3646206386fa
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/27/2020
ms.locfileid: "85467625"
---
# <a name="idiaenumsymbolsbyaddrsymbolbyrva"></a>IDiaEnumSymbolsByAddr::symbolByRVA
Umieszcza moduł wyliczający przez przeszukiwanie według względnych adresów wirtualnych (RVA).

## <a name="syntax"></a>Składnia

```C++
HRESULT symbolByRVA ( 
   DWORD**      relativeVirtualAddress,
   IDiaSymbol** ppsymbol
);
```

#### <a name="parameters"></a>Parametry
 relativeVirtualAddress

podczas Adres względem początku obrazu.

 ppsymbol

określoną Zwraca obiekt [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md) reprezentujący znaleziony symbol.

## <a name="return-value"></a>Wartość zwracana
 Jeśli powiedzie się, zwraca `S_OK` . Zwraca `S_FALSE` czy nie można znaleźć symbolu. W przeciwnym razie zwraca kod błędu.

## <a name="see-also"></a>Zobacz też
- [IDiaEnumSymbolsByAddr](../../debugger/debug-interface-access/idiaenumsymbolsbyaddr.md)
- [IDiaEnumSymbolsByAddr::symbolByVA](../../debugger/debug-interface-access/idiaenumsymbolsbyaddr-symbolbyva.md)
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)