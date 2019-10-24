---
title: 'IDiaSymbol:: get_unmodifiedType | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_unmodifiedType method
ms.assetid: bf914dc0-ff84-4f5d-9f75-1733b17f3be0
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 47841f5fe4abeafe7c522784db337b1960081439
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/22/2019
ms.locfileid: "72738984"
---
# <a name="idiasymbolget_unmodifiedtype"></a>IDiaSymbol::get_unmodifiedType
Pobiera oryginalny typ dla tego symbolu. Użyj, gdy [Wyliczenie SymTagEnum —](../../debugger/debug-interface-access/symtagenum.md) jest ustawione na typ.

## <a name="syntax"></a>Składnia

```C++
HRESULT get_unmodifiedType( 
   IDiaSymbol** pRetVal
);
```

#### <a name="parameters"></a>Parametry
 `pRetVal`

określoną Zwraca obiekt [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md) , który reprezentuje oryginalny typ tego symbolu.

## <a name="return-value"></a>Wartość zwracana
 Jeśli powiedzie się, zwraca `S_OK`; w przeciwnym razie zwraca `S_FALSE` lub kod błędu.

> [!NOTE]
> Wartość zwracana `S_FALSE` oznacza, że właściwość nie jest dostępna dla symbolu.

## <a name="remarks"></a>Uwagi
 Bieżący typ jest modyfikacją zwróconego oryginalnego typu. Oryginalny typ symbolu można określić, najpierw pobierając typ symbolu, a następnie interrogating, który zwraca typ dla oryginalnego typu. Należy zauważyć, że niektóre symbole nie mogą mieć zmodyfikowanego typu oryginalnego typu.

## <a name="requirements"></a>Wymagania
 Nagłówek: dia2. h

 Biblioteka: diaguids. lib

 DLL: msdia100. dll

## <a name="see-also"></a>Zobacz także
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)