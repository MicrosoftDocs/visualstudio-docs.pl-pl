---
title: 'IDiaSymbol:: get_objectFileName | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
ms.assetid: 21793872-4879-4e4d-b527-dcf70aa7fb31
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 351efbd1f8beaf40ef0b50a450b1fe03cd8832e4
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99853801"
---
# <a name="idiasymbolget_objectfilename"></a>IDiaSymbol::get_objectFileName
Pobiera nazwę pliku obiektu.

## <a name="syntax"></a>Składnia

```C++
HRESULT get_objectFilename(
   BSTR *pRetVal);
```

#### <a name="parameters"></a>Parametry
 `pRetVal`

określoną Wskaźnik do elementu `BSTR` , który zawiera nazwę pliku obiektu.

## <a name="return-value"></a>Wartość zwracana
 Jeśli powiedzie się, zwraca `S_OK` ; w przeciwnym razie zwraca `S_FALSE` lub kod błędu.

## <a name="see-also"></a>Zobacz też
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)