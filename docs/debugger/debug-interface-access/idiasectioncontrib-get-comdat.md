---
description: Pobiera flagę wskazującą, czy sekcja jest rekordem COMDAT.
title: 'IDiaSectionContrib:: get_comdat | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSectionContrib::get_comdat method
ms.assetid: 8bd9be8d-59ee-4698-b055-daba354b8dcc
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 83d3672ed0ec0b55d8c0bbc25ce25ea57f896c73
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/05/2021
ms.locfileid: "102157323"
---
# <a name="idiasectioncontribget_comdat"></a>IDiaSectionContrib::get_comdat
Pobiera flagę wskazującą, czy sekcja jest rekordem COMDAT.

## <a name="syntax"></a>Składnia

```C++
HRESULT get_comdat ( 
   BOOL* pRetVal
);
```

#### <a name="parameters"></a>Parametry
 `pRetVal`

określoną Zwraca `TRUE` czy sekcja jest rekordem COMDAT; w przeciwnym razie zwraca `FALSE` .

## <a name="return-value"></a>Wartość zwracana
 Jeśli powiedzie się, zwraca `S_OK` . Zwraca wartość, `S_FALSE` Jeśli ta właściwość nie jest obsługiwana. W przeciwnym razie zwraca kod błędu.

## <a name="remarks"></a>Uwagi
 Rekord COMDAT jest rekordem Common Object Format (COFF), który sprawia, że spakowane funkcje widoczne dla konsolidatora.

## <a name="see-also"></a>Zobacz też
- [IDiaSectionContrib](../../debugger/debug-interface-access/idiasectioncontrib.md)
