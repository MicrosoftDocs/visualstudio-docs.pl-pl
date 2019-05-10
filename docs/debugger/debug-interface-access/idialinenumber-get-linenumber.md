---
title: Idialinenumber::get_linenumber — | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaLineNumber::get_lineNumber method
ms.assetid: 2dff3fd9-097d-4645-bc1b-cb65ecbc42a6
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 77a1554e749e6f5186f7c99844cb793814b0129b
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62839839"
---
# <a name="idialinenumbergetlinenumber"></a>IDiaLineNumber::get_lineNumber
Pobiera numer wiersza w pliku źródłowym.

## <a name="syntax"></a>Składnia

```C++
HRESULT get_lineNumber ( 
   DWORD* pRetVal
);
```

#### <a name="parameters"></a>Parametry
 `pRetVal`

[out] Zwraca numer wiersza w pliku źródłowym.

## <a name="return-value"></a>Wartość zwracana
 Jeśli operacja się powiedzie, zwraca `S_OK`. Zwraca `S_FALSE` Jeśli ta właściwość nie jest obsługiwana. W przeciwnym razie zwraca kod błędu.

## <a name="example"></a>Przykład

```C++
CComPtr< IDiaLineNumber> pLine;
DWORD linenum;
pLine->get_lineNumber( &linenum );
```

## <a name="see-also"></a>Zobacz też
- [IDiaLineNumber](../../debugger/debug-interface-access/idialinenumber.md)