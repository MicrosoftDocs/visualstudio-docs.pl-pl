---
title: 'IDiaFrameData:: get_functionStart | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaFrameData::get_functionStart method
ms.assetid: 49fd24fb-65c2-4812-8303-56a968353e1b
caps.latest.revision: 12
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 08029b3abc3ec054cd8244d22d17db7992fa3623
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "68186947"
---
# <a name="idiaframedataget_functionstart"></a>IDiaFrameData::get_functionStart
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Pobiera flagę wskazującą, czy blok zawiera punkt wejścia funkcji.  
  
## <a name="syntax"></a>Składnia  
  
```cpp#  
HRESULT get_functionStart (   
   BOOL* pRetVal  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pRetVal`  
 określoną Zwraca `TRUE` czy blok zawiera punkt wejścia; w przeciwnym razie zwraca `FALSE` .  
  
## <a name="return-value"></a>Wartość zwracana  
 Jeśli powiedzie się, zwraca `S_OK` . Zwraca wartość, `S_FALSE` Jeśli ta właściwość nie jest obsługiwana. W przeciwnym razie zwraca kod błędu.  
  
## <a name="remarks"></a>Uwagi  
 Jest możliwe, że ramka stosu nie jest początkiem funkcji, ponieważ ramka reprezentuje wbudowaną metodę lub funkcję wstawioną do funkcji.  
  
## <a name="see-also"></a>Zobacz też  
 [IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md)
