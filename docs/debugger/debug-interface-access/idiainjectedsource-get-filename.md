---
title: 'IDiaInjectedSource:: get_filename | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
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
ms.openlocfilehash: cc7a1ced59f2a1126df1cf2db3348d9d26fb1461
ms.sourcegitcommit: 66f31cc4ce1236e638ab58d2f70d3646206386fa
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/27/2020
ms.locfileid: "85467072"
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
 Jeśli powiedzie się, zwraca `S_OK` . Zwraca wartość, `S_FALSE` Jeśli ta właściwość nie jest obsługiwana. W przeciwnym razie zwraca kod błędu.

## <a name="see-also"></a>Zobacz też
- [IDiaInjectedSource](../../debugger/debug-interface-access/idiainjectedsource.md)