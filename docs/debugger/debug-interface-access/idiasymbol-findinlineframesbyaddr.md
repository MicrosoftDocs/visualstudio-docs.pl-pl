---
title: 'IDiaSymbol:: findInlineFramesByAddr | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
ms.assetid: 36a122e6-f27e-40cd-9784-cdaf279e1905
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 0b178a984ce915ace20b306ea2594031262aceac
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99863684"
---
# <a name="idiasymbolfindinlineframesbyaddr"></a>IDiaSymbol::findInlineFramesByAddr
Pobiera wyliczenie, które pozwala klientowi na iterację we wszystkich wbudowanych ramkach na danym adresie.

## <a name="syntax"></a>Składnia

```C++
HRESULT findInlineFramesByAddr ( 
   DWORD             isect,
   DWORD             offset,
   IDiaEnumSymbols** ppResult
);
```

#### <a name="parameters"></a>Parametry
 `isect`

podczas Określa składnik sekcji adresu.

 `offset`

podczas Określa składnik przesunięcia adresu.

 `ppResult`

określoną Zawiera `IDiaEnumSymbols` obiekt zawierający listę pobieranych ramek.

## <a name="return-value"></a>Wartość zwracana
 Jeśli powiedzie się, zwraca `S_OK` ; w przeciwnym razie zwraca kod błędu.

## <a name="see-also"></a>Zobacz też
- [IDiaSession](../../debugger/debug-interface-access/idiasession.md)
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
- [SymTagEnum, wyliczenie](../../debugger/debug-interface-access/symtagenum.md)
- [IDiaEnumSymbols](../../debugger/debug-interface-access/idiaenumsymbols.md)