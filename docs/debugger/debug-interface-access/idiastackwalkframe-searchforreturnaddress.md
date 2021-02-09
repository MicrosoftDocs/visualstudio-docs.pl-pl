---
title: 'IDiaStackWalkFrame:: Searchforreturnaddress — | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaStackWalkFrame::searchForReturnAddress method
ms.assetid: 1a54c50d-94af-4a43-ac4e-d80c5df156c3
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 409aef9c6516c3804cd2b35df012d2494cecdbbb
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99863838"
---
# <a name="idiastackwalkframesearchforreturnaddress"></a>IDiaStackWalkFrame::searchForReturnAddress
Przeszukuje określoną ramkę stosu dla najbliższego adresu zwrotnego funkcji.

## <a name="syntax"></a>Składnia

```C++
HRESULT searchForReturnAddress ( 
   IDiaFrameData* frame,
   ULONGLONG*     returnAddress
);
```

#### <a name="parameters"></a>Parametry
 `frame`

podczas Obiekt [IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md) , który reprezentuje bieżącą ramkę stosu.

 `returnAddress`

określoną Zwraca najbliższy zwrotny adres funkcji.

## <a name="return-value"></a>Wartość zwracana
 Jeśli powiedzie się, zwraca `S_OK` ; w przeciwnym razie zwraca kod błędu.

## <a name="see-also"></a>Zobacz też
- [IDiaStackWalkFrame](../../debugger/debug-interface-access/idiastackwalkframe.md)
- [IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md)