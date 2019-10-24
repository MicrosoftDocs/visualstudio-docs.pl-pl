---
title: 'IDiaSession:: findAcceleratorInlineesByLinenum | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: 386c87aa-f7b2-4d38-9dd6-fffba9ff01f0
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 6d08168a83b9bb635fd6a0e22dc22f91a454001f
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/22/2019
ms.locfileid: "72742321"
---
# <a name="idiasessionfindacceleratorinlineesbylinenum"></a>IDiaSession::findAcceleratorInlineesByLinenum
Zwraca Wyliczenie symboli dla ramek wbudowanych, które odpowiadają określonej lokalizacji źródłowej.

## <a name="syntax"></a>Składnia

```C++
HRESULT findAcceleratorInlineeLinesByName ( 
   IDiaSymbol*           parent,
   IDiaSourceFile*       file,
   DWORD                 linenum,
   DWORD                 colnum,
   IDiaEnumLineNumbers** ppResult
);
```

#### <a name="parameters"></a>Parametry
 `parent`

podczas @No__t_0, która odnosi się do funkcji zastępczej akceleratora, która musi być przeszukiwana.

 `file`

podczas @No__t_0 lokalizacji źródłowej.

 `linenum`

podczas Numer wiersza lokalizacji źródłowej.

 `colnum`

podczas Numer kolumny lokalizacji źródłowej.

 `ppResult`

określoną Wskaźnik do `IDiaEnumLineNumbers` wskaźnika interfejsu, który jest inicjowany z wynikiem.

## <a name="return-value"></a>Wartość zwracana
 Jeśli powiedzie się, zwraca `S_OK`; w przeciwnym razie zwraca kod błędu.

## <a name="see-also"></a>Zobacz także
- [IDiaSession](../../debugger/debug-interface-access/idiasession.md)
- [IDiaEnumLineNumbers](../../debugger/debug-interface-access/idiaenumlinenumbers.md)
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)