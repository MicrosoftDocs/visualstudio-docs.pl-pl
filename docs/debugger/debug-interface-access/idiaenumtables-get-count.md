---
description: Pobiera liczbę tabel.
title: 'IDiaEnumTables:: get_Count | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumTables::get_Count method
ms.assetid: 30fa316b-a746-4028-acae-4efcd2066f38
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: c69e1860e3a0b534e53d5431c77cdfa3753a6da1
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/05/2021
ms.locfileid: "102157862"
---
# <a name="idiaenumtablesget_count"></a>IDiaEnumTables::get_Count
Pobiera liczbę tabel.

## <a name="syntax"></a>Składnia

```C++
HRESULT get_Count (    LONG* pRetVal
);

```

#### <a name="parameters"></a>Parametry
 `pRetVal`

określoną Zwraca liczbę tabel.

## <a name="return-value"></a>Wartość zwracana
 Jeśli powiedzie się, zwraca `S_OK` ; w przeciwnym razie zwraca kod błędu.

## <a name="see-also"></a>Zobacz też
- [IDiaEnumTables](../../debugger/debug-interface-access/idiaenumtables.md)
- [IDiaEnumTables::Item](../../debugger/debug-interface-access/idiaenumtables-item.md)
