---
title: 'IDiaEnumSegments:: Next | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumSegments::Next method
ms.assetid: 53f61874-d821-47ab-a1f5-27e982804a6a
caps.latest.revision: 10
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: e00f85d4b3a111f3a68b934006a32197245d4d6e
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "68189877"
---
# <a name="idiaenumsegmentsnext"></a>IDiaEnumSegments::Next
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Pobiera określoną liczbę segmentów w sekwencji wyliczenia.  
  
## <a name="syntax"></a>Składnia  
  
```cpp#  
HRESULT Next (   
   ULONG         celt,   
   IDiaSegment** rgelt,  
   ULONG*        pceltFetched  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 celt  
 podczas Liczba segmentów w module wyliczającym do pobrania.  
  
 rgelt  
 określoną Tablica, która ma zostać wypełniona przy użyciu żądanych obiektów [IDiaSegment](../../debugger/debug-interface-access/idiasegment.md) , które reprezentują segmenty.  
  
 pceltFetched  
 określoną Zwraca liczbę segmentów z pobranego modułu wyliczającego.  
  
## <a name="return-value"></a>Wartość zwracana  
 Jeśli powiedzie się, zwraca `S_OK` . Zwraca `S_FALSE` czy nie ma więcej segmentów. W przeciwnym razie zwraca kod błędu.  
  
## <a name="see-also"></a>Zobacz też  
 [IDiaEnumSegments](../../debugger/debug-interface-access/idiaenumsegments.md)   
 [IDiaSegment](../../debugger/debug-interface-access/idiasegment.md)
