---
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
ms.openlocfilehash: 1a2ce0d808a21a793115c6f065ca4ab95b1507e5
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99855236"
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