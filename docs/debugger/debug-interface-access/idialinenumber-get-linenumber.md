---
title: 'IDiaLineNumber:: get_lineNumber | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
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
ms.openlocfilehash: 172ef1631dedc3caf90d3facf1d2061dc8590fa4
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "85466883"
---
# <a name="idialinenumberget_linenumber"></a>IDiaLineNumber::get_lineNumber
Pobiera numer wiersza w pliku źródłowym.

## <a name="syntax"></a>Składnia

```C++
HRESULT get_lineNumber ( 
   DWORD* pRetVal
);
```

#### <a name="parameters"></a>Parametry
 `pRetVal`

określoną Zwraca numer wiersza w pliku źródłowym.

## <a name="return-value"></a>Wartość zwracana
 Jeśli powiedzie się, zwraca `S_OK` . Zwraca wartość, `S_FALSE` Jeśli ta właściwość nie jest obsługiwana. W przeciwnym razie zwraca kod błędu.

## <a name="example"></a>Przykład

```C++
CComPtr< IDiaLineNumber> pLine;
DWORD linenum;
pLine->get_lineNumber( &linenum );
```

## <a name="see-also"></a>Zobacz też
- [IDiaLineNumber](../../debugger/debug-interface-access/idialinenumber.md)