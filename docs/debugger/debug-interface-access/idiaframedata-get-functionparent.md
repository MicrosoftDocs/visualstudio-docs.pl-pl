---
title: 'IDiaFrameData:: get_functionParent | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaFrameData::get_functionParent method
ms.assetid: f00b9ab1-d4da-4818-973a-58f8f0e66769
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: ef646016433ecfe19106a17dff391c2dd8ce8382
ms.sourcegitcommit: 66f31cc4ce1236e638ab58d2f70d3646206386fa
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/27/2020
ms.locfileid: "85467387"
---
# <a name="idiaframedataget_functionparent"></a>IDiaFrameData::get_functionParent
Pobiera interfejs danych ramek dla otaczającej funkcji.

## <a name="syntax"></a>Składnia

```C++
HRESULT get_functionParent ( 
   IDiaFrameData** pRetVal
);
```

#### <a name="parameters"></a>Parametry
 `pRetVal`

określoną Zwraca obiekt [IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md) dla otaczającej funkcji.

## <a name="return-value"></a>Wartość zwracana
 Jeśli powiedzie się, zwraca `S_OK` ; w przeciwnym razie zwraca kod błędu.

## <a name="see-also"></a>Zobacz też
- [IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md)