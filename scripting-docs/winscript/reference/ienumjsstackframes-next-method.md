---
title: IEnumJsStackFrames::Next, metoda | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IEnumJsStackFrames.Next
apilocation:
- jscript9diag.dll
ms.assetid: efceb3a1-9239-4f55-9cbb-94670679988b
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 94e3f478654fadec152aba0690a5474ebbfe02f5
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2019
ms.locfileid: "58159065"
---
# <a name="ienumjsstackframesnext-method"></a>IEnumJsStackFrames::Next — Metoda
Pobiera określoną liczbę klatek.  
  
## <a name="syntax"></a>Składnia  
  
```cpp
HRESULT Next(  
   ULONG cFrameCount,  
   JS_NATIVE_FRAME *pFrames,  
   ULONG *pcFetched  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `cFrameCount`  
 [in] Liczba ramek do pobrania.  
  
 `pFrames`  
 [out] Tablica do przechowywania ramek.  
  
 `pcFetched`  
 [out] Liczba zwróconych ramek.  
  
## <a name="return-value"></a>Wartość zwracana  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** jscript9diag.h  
  
## <a name="see-also"></a>Zobacz też  
 [IEnumJsStackFrames, interfejs](../../winscript/reference/ienumjsstackframes-interface.md)