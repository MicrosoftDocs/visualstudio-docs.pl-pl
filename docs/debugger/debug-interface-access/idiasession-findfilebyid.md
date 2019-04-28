---
title: Idiasession::findfilebyid — | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSession::findFileById method
ms.assetid: 710efe04-78b5-4f3e-a1d8-f9b069063503
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: e3454ff5ef087b67dda5d48849d4a6c4eceb7e52
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62839358"
---
# <a name="idiasessionfindfilebyid"></a>IDiaSession::findFileById
Pobiera pliku źródłowego przez identyfikator pliku źródłowego.

## <a name="syntax"></a>Składnia

```C++
HRESULT findFileById ( 
   DWORD            uniqueId,
   IDiaSourceFile** ppResult
);
```

#### <a name="parameters"></a>Parametry
 `uniqueId`

[in] Określa identyfikator pliku źródłowego.

 `ppResult`

[out] Zwraca [idiasourcefile —](../../debugger/debug-interface-access/idiasourcefile.md) pobrać obiekt, który reprezentuje plik źródłowy.

## <a name="return-value"></a>Wartość zwracana
 Jeśli operacja się powiedzie, zwraca `S_OK`; w przeciwnym razie zwraca kod błędu.

## <a name="remarks"></a>Uwagi
 Identyfikator pliku źródłowego jest używana wewnętrznie w celu DIA SDK unikatowość wszystkich plików źródłowych unikatową wartość. Ta metoda jest zwykle używana wewnętrznie w celu DIA SDK.

## <a name="see-also"></a>Zobacz też
- [IDiaSession](../../debugger/debug-interface-access/idiasession.md)
- [IDiaSession::findFile](../../debugger/debug-interface-access/idiasession-findfile.md)
- [IDiaSourceFile](../../debugger/debug-interface-access/idiasourcefile.md)