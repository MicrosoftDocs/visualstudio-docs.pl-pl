---
title: 'IDiaInjectedSource:: get_filename | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaInjectedSource::get_filename method
ms.assetid: 20f4fc68-335a-4971-b3a6-76501f0e8b19
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 3aa2929ac592d475896eff0c1969115f971a8572
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/22/2019
ms.locfileid: "72743376"
---
# <a name="idiainjectedsourceget_filename"></a>IDiaInjectedSource::get_filename
Pobiera nazwę pliku źródła.

## <a name="syntax"></a>Składnia

```C++
HRESULT get_filename ( 
   BSTR* pRetVal
);
```

#### <a name="parameters"></a>Parametry
 pRetVal

określoną Zwraca nazwę pliku źródła.

## <a name="return-value"></a>Wartość zwracana
 Jeśli powiedzie się, zwraca `S_OK`. Zwraca `S_FALSE`, jeśli ta właściwość nie jest obsługiwana. W przeciwnym razie zwraca kod błędu.

## <a name="see-also"></a>Zobacz także
- [IDiaInjectedSource](../../debugger/debug-interface-access/idiainjectedsource.md)