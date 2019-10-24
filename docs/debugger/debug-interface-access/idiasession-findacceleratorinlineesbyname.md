---
title: 'IDiaSession:: findAcceleratorInlineesByName | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: e203e5c2-6563-43fa-be56-3063955043ab
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 007477d3f0de3767b0c5ef0af977f969505884ed
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/22/2019
ms.locfileid: "72742311"
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

podczas Opcja wyszukiwania nazw, która będzie używana podczas wyszukiwania ramek wbudowanych, które odpowiadają `name`. Aby uzyskać więcej informacji, zobacz [Namesearchoptions — Enumeration](../../debugger/debug-interface-access/namesearchoptions.md).

 `ppResult`

określoną Wskaźnik do `IDiaEnumSymbols` wskaźnika interfejsu, który jest inicjowany z wynikiem.

## <a name="return-value"></a>Wartość zwracana
 Jeśli powiedzie się, zwraca `S_OK`; w przeciwnym razie zwraca kod błędu.

## <a name="remarks"></a>Uwagi
 Ta funkcja wyszukuje konspekty tylko w funkcjach zastępczych akceleratora. Ignoruje natywne C++ rekordy procedur.

## <a name="see-also"></a>Zobacz także
- [IDiaSession](../../debugger/debug-interface-access/idiasession.md)
- [IDiaEnumSymbols](../../debugger/debug-interface-access/idiaenumsymbols.md)
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)