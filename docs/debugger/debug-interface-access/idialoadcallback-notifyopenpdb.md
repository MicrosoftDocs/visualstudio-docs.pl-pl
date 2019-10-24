---
title: 'IDiaLoadCallback:: NotifyOpenPDB | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaLoadCallback::NotifyOpenPDB method
ms.assetid: c0547f99-8468-4e57-82ca-9ef7d6707c8a
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: cbcf8aff8dc18776cbcb09a5fa3f13edca4cd7a7
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/22/2019
ms.locfileid: "72743066"
---
# <a name="idialoadcallbacknotifyopenpdb"></a>IDiaLoadCallback::NotifyOpenPDB
Wywoływana, gdy zostanie otwarty plik kandydata. pdb.

## <a name="syntax"></a>Składnia

```C++
HRESULT NotifyOpenPDB ( 
   LPCOLESTR pdbPath,
   HRESULT   resultCode
);
```

#### <a name="parameters"></a>Parametry
 `pdbPath`

podczas Pełna ścieżka pliku. pdb.

 `resultCode`

podczas Kod określający powodzenie (`S_OK`) lub niepowodzenie ładowania zgodnie z zastosowanym dla tego pliku.

## <a name="return-value"></a>Wartość zwracana
 Jeśli powiedzie się, zwraca `S_OK`; w przeciwnym razie zwraca kod błędu. Kod powrotny jest zwykle ignorowany.

## <a name="see-also"></a>Zobacz także
- [IDiaLoadCallback2](../../debugger/debug-interface-access/idialoadcallback2.md)