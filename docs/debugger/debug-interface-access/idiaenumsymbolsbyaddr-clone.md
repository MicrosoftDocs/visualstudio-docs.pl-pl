---
title: 'IDiaEnumSymbolsByAddr:: Clone | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumSymbolsByAddr::Clone method
ms.assetid: f4582c69-bc3f-4a26-bcca-b641102b85fe
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 6f81525147b30548184ae68c0ed3259d093a6685
ms.sourcegitcommit: 66f31cc4ce1236e638ab58d2f70d3646206386fa
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/27/2020
ms.locfileid: "85467674"
---
# <a name="idiaenumsymbolsbyaddrclone"></a>IDiaEnumSymbolsByAddr::Clone
Tworzy kopię obiektu.

## <a name="syntax"></a>Składnia

```C++
HRESULT Clone ( 
   IDiaEnumSymbolsByAddr** ppenum
);
```

#### <a name="parameters"></a>Parametry
 ppenum

określoną Zwraca obiekt [IDiaEnumSymbolsByAddr](../../debugger/debug-interface-access/idiaenumsymbolsbyaddr.md) , który zawiera duplikat modułu wyliczającego. Symbole nie są duplikowane, tylko moduł wyliczający.

## <a name="return-value"></a>Wartość zwracana
 Jeśli powiedzie się, zwraca `S_OK` ; w przeciwnym razie zwraca kod błędu.

## <a name="see-also"></a>Zobacz też
- [IDiaEnumSymbolsByAddr](../../debugger/debug-interface-access/idiaenumsymbolsbyaddr.md)