---
title: 'IDiaStackWalkHelper:: Searchforreturnaddress — | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaStackWalkHelper2::searchForReturnAddress method
ms.assetid: 904223b1-6e26-4980-b310-d0b222cdbbbd
caps.latest.revision: 12
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: f2e2be83308e3328707d0f91c417d77ac3dd074d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "62563093"
---
# <a name="idiastackwalkhelpersearchforreturnaddress"></a>IDiaStackWalkHelper::searchForReturnAddress
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Przeszukuje określoną ramkę stosu dla najbliższego adresu zwrotnego funkcji.  
  
## <a name="syntax"></a>Składnia  
  
```cpp#  
HRESULT searchForReturnAddress(   
   IDiaFrameData*  frame,  
   ULONGLONG*      returnAddress  
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
 [IDiaStackWalkHelper](../../debugger/debug-interface-access/idiastackwalkhelper.md)   
 [IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md)
