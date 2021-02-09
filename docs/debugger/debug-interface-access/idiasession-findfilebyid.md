---
title: 'IDiaSession:: findFileById | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSession::findFileById method
ms.assetid: 710efe04-78b5-4f3e-a1d8-f9b069063503
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 172a02a2b2d818132131b94192af39d45e390254
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99864258"
---
# <a name="idiasessionfindfilebyid"></a>IDiaSession::findFileById
Pobiera plik źródłowy według identyfikatora pliku źródłowego.

## <a name="syntax"></a>Składnia

```C++
HRESULT findFileById ( 
   DWORD            uniqueId,
   IDiaSourceFile** ppResult
);
```

#### <a name="parameters"></a>Parametry
 `uniqueId`

podczas Określa identyfikator pliku źródłowego.

 `ppResult`

określoną Zwraca obiekt [IDiaSourceFile](../../debugger/debug-interface-access/idiasourcefile.md) , który reprezentuje pobrany plik źródłowy.

## <a name="return-value"></a>Wartość zwracana
 Jeśli powiedzie się, zwraca `S_OK` ; w przeciwnym razie zwraca kod błędu.

## <a name="remarks"></a>Uwagi
 Identyfikator pliku źródłowego jest unikatową wartością używaną wewnętrznie do DIA SDK, aby wszystkie pliki źródłowe były unikatowe. Ta metoda jest zwykle używana wewnętrznie w DIA SDK.

## <a name="see-also"></a>Zobacz też
- [IDiaSession](../../debugger/debug-interface-access/idiasession.md)
- [IDiaSession::findFile](../../debugger/debug-interface-access/idiasession-findfile.md)
- [IDiaSourceFile](../../debugger/debug-interface-access/idiasourcefile.md)