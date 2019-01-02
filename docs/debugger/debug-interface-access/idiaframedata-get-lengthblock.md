---
title: Idiaframedata::get_lengthblock — | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaFrameData::get_lengthBlock method
ms.assetid: 2e54deb7-7744-428e-913c-1d47a2aa89b0
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 2e2eafc0737a1bb93df73b7648734d1f1c77708a
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/02/2019
ms.locfileid: "53875958"
---
# <a name="idiaframedatagetlengthblock"></a>IDiaFrameData::get_lengthBlock
Pobiera długość w bajtach, w bloku kodu opisanego przez ramkę.  
  
## <a name="syntax"></a>Składnia  
  
```C++  
HRESULT get_lengthBlock (   
   DWORD* pRetVal  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pRetVal`  
 [out] Zwraca liczbę bajtów kodu w ramce.  
  
## <a name="return-value"></a>Wartość zwracana  
 Jeśli operacja się powiedzie, zwraca `S_OK`. Zwraca `S_FALSE` Jeśli ta właściwość nie jest obsługiwana. W przeciwnym razie zwraca kod błędu.  
  
## <a name="remarks"></a>Uwagi  
 Wartość zwrócona przez tę metodę jest zwykle używanych w interpretacji ciągu program (zobacz [idiaframedata::get_program —](../../debugger/debug-interface-access/idiaframedata-get-program.md) metody dla definicji ciąg program).  
  
## <a name="see-also"></a>Zobacz też  
 [Idiaframedata —](../../debugger/debug-interface-access/idiaframedata.md)   
 [IDiaFrameData::get_program](../../debugger/debug-interface-access/idiaframedata-get-program.md)