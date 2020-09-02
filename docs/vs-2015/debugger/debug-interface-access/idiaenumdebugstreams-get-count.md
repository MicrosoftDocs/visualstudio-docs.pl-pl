---
title: 'IDiaEnumDebugStreams:: get_Count | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumDebugStreams::get_Count method
ms.assetid: 5c13fa9a-b35e-47b0-806f-1f53bfe1ba89
caps.latest.revision: 11
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 238fa1386184f7ce6b0cd0ce54334fb52f29a638
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "68187342"
---
# <a name="idiaenumdebugstreamsget_count"></a>IDiaEnumDebugStreams::get_Count
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Pobiera liczbę strumieni debugowania.  
  
## <a name="syntax"></a>Składnia  
  
```cpp#  
HRESULT get_Count(   
   LONG* pRetVal  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pRetVal`  
 określoną Zwraca liczbę strumieni debugowania dostępnych w tym module wyliczającym.  
  
## <a name="return-value"></a>Wartość zwracana  
 Jeśli powiedzie się, zwraca `S_OK` ; w przeciwnym razie zwraca kod błędu.  
  
## <a name="see-also"></a>Zobacz też  
 [IDiaEnumDebugStreams](../../debugger/debug-interface-access/idiaenumdebugstreams.md)   
 [IDiaEnumDebugStreams::Item](../../debugger/debug-interface-access/idiaenumdebugstreams-item.md)
