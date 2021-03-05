---
description: Zwraca Wyliczenie symboli dla ramek wbudowanych odpowiadających określonej nazwie funkcji wbudowanej.
title: 'IDiaSession:: findAcceleratorInlineesByName | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
ms.assetid: e203e5c2-6563-43fa-be56-3063955043ab
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: fb2a6c67dc9f16d3a4ef98d36772681d3ab2638e
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/05/2021
ms.locfileid: "102159028"
---
# <a name="idiasessionfindacceleratorinlineesbyname"></a>IDiaSession::findAcceleratorInlineesByName
Zwraca Wyliczenie symboli dla ramek wbudowanych odpowiadających określonej nazwie funkcji wbudowanej.

## <a name="syntax"></a>Składnia

```C++
HRESULT findAcceleratorInlineeLinesByName ( 
   LPCOLESTR             name,
   DWORD                 option,
   IDiaEnumSymbols**     ppResult
);
```

#### <a name="parameters"></a>Parametry
 `name`

podczas Nazwa funkcji inline, która ma być przeszukiwana.

 `option`

podczas Opcje wyszukiwania nazw, które mają być używane podczas wyszukiwania ramek wbudowanych, które odpowiadają `name` . Aby uzyskać więcej informacji, zobacz [Namesearchoptions — Enumeration](../../debugger/debug-interface-access/namesearchoptions.md).

 `ppResult`

określoną Wskaźnik do `IDiaEnumSymbols` wskaźnika interfejsu, który jest inicjowany z wynikiem.

## <a name="return-value"></a>Wartość zwracana
 Jeśli powiedzie się, zwraca `S_OK` ; w przeciwnym razie zwraca kod błędu.

## <a name="remarks"></a>Uwagi
 Ta funkcja wyszukuje konspekty tylko w funkcjach zastępczych akceleratora. Ignoruje natywne rekordy procedur języka C++.

## <a name="see-also"></a>Zobacz też
- [IDiaSession](../../debugger/debug-interface-access/idiasession.md)
- [IDiaEnumSymbols](../../debugger/debug-interface-access/idiaenumsymbols.md)
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
