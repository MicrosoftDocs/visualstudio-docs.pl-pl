---
title: 'IDiaSession:: findInlineFramesByRVA | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: ddb3ff0e-cb3d-4fa0-af56-f064b218b264
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 329bf9f4fa94171347eeea8fc9f2744b7ce4269f
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/22/2019
ms.locfileid: "72742155"
---
# <a name="idiasessionfindinlineframesbyrva"></a>IDiaSession::findInlineFramesByRVA
Pobiera wyliczenie, które pozwala klientowi na iterację we wszystkich wbudowanych ramkach w określonym względnym adresie wirtualnym (RVA).

## <a name="syntax"></a>Składnia

```C++
HRESULT findInlineFramesByRVA ( 
   IDiaSymbol*       parent,   DWORD             rva,
   IDiaEnumSymbols** ppResult
);
```

#### <a name="parameters"></a>Parametry
 `parent`

podczas Obiekt `IDiaSymbol` reprezentujący element nadrzędny.

 `rva`

podczas Określa adres jako RVA.

 `ppResult`

określoną Przechowuje `IDiaEnumSymbols` obiektu, który zawiera listę pobieranych ramek.

## <a name="return-value"></a>Wartość zwracana
 Jeśli powiedzie się, zwraca `S_OK`; w przeciwnym razie zwraca kod błędu.

## <a name="see-also"></a>Zobacz także
- [IDiaSession](../../debugger/debug-interface-access/idiasession.md)
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
- [SymTagEnum, wyliczenie](../../debugger/debug-interface-access/symtagenum.md)
- [IDiaEnumSymbols](../../debugger/debug-interface-access/idiaenumsymbols.md)