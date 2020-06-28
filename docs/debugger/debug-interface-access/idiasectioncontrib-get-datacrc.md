---
title: 'IDiaSectionContrib:: get_dataCrc | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSectionContrib::get_dataCrc method
ms.assetid: 33b7488f-dc9c-47b3-b08c-737e0eb1bf7d
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 612c074528b2d78d16117f1a8c78044b1420a980
ms.sourcegitcommit: 66f31cc4ce1236e638ab58d2f70d3646206386fa
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/27/2020
ms.locfileid: "85466281"
---
# <a name="idiasectioncontribget_datacrc"></a>IDiaSectionContrib::get_dataCrc
Pobiera cykliczne sprawdzenie nadmiarowości (CRC) danych w sekcji.

## <a name="syntax"></a>Składnia

```C++
HRESULT get_dataCrc ( 
   DWORD* pRetVal
);
```

#### <a name="parameters"></a>Parametry
 `pRetVal`

określoną Zwraca wartość CRC danych w sekcji.

## <a name="return-value"></a>Wartość zwracana
 Jeśli powiedzie się, zwraca `S_OK` . Zwraca wartość, `S_FALSE` Jeśli ta właściwość nie jest obsługiwana. W przeciwnym razie zwraca kod błędu.

## <a name="see-also"></a>Zobacz też
- [IDiaSectionContrib](../../debugger/debug-interface-access/idiasectioncontrib.md)