---
title: Idiaframedata::get_type — | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaFrameData::get_type method
ms.assetid: efca38b5-c479-4d0a-a164-f903f25c5509
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 9ee35b5884696d2d9faade5ceb2ec16945d3991c
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/02/2019
ms.locfileid: "53837566"
---
# <a name="idiaframedatagettype"></a>IDiaFrameData::get_type
Pobiera typ ramki specyficznych dla kompilatora.  
  
## <a name="syntax"></a>Składnia  
  
```C++  
HRESULT get_type (   
   DWORD* pRetVal  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pRetVal`  
 [out] Zwraca wartość z zakresu od [stackframetypeenum — wyliczenie](../../debugger/debug-interface-access/stackframetypeenum.md) wyliczenie, które wskazuje typ ramki specyficznych dla kompilatora.  
  
## <a name="return-value"></a>Wartość zwracana  
 Jeśli operacja się powiedzie, zwraca `S_OK`. Zwraca `S_FALSE` Jeśli ta właściwość nie jest obsługiwana. W przeciwnym razie zwraca kod błędu.  
  
## <a name="see-also"></a>Zobacz też  
 [Idiaframedata —](../../debugger/debug-interface-access/idiaframedata.md)   
 [StackFrameTypeEnum, wyliczenie](../../debugger/debug-interface-access/stackframetypeenum.md)