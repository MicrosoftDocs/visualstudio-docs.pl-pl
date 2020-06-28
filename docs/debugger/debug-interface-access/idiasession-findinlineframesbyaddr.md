---
title: 'IDiaSession:: findInlineFramesByAddr | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
ms.assetid: e7dc1ac7-bb09-45be-96d2-365a9b7336e4
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 94d910f49120fcbf22f4d6830d2bd89eeb3492af
ms.sourcegitcommit: 66f31cc4ce1236e638ab58d2f70d3646206386fa
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/27/2020
ms.locfileid: "85465700"
---
# <a name="idiasessionfindinlineframesbyaddr"></a>IDiaSession::findInlineFramesByAddr
Pobiera wyliczenie, które pozwala klientowi na iterację we wszystkich wbudowanych ramkach na danym adresie.

## <a name="syntax"></a>Składnia

```C++
HRESULT findInlineFramesByAddr ( 
   IDiaSymbol*       parent,   DWORD             isect,
   DWORD             offset,
   IDiaEnumSymbols** ppResult
);
```

#### <a name="parameters"></a>Parametry
 `parent`

podczas `IDiaSymbol`Obiekt reprezentujący element nadrzędny.

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