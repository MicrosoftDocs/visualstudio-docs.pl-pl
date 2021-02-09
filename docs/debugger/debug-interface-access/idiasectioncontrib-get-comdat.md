---
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
ms.openlocfilehash: 44397558b29b1dd2e8038fa2d9b5fec44b5404df
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99855481"
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