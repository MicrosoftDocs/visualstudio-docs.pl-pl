---
title: 'IDiaInjectedSource:: get_objectFilename | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaInjectedSource::get_objectFilename method
ms.assetid: 7c42847a-f0df-443a-a9fe-c495c1271ea8
caps.latest.revision: 11
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: f485fb52c2de36e111fe2846a9ee16328ac61c49
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "68192409"
---
# <a name="idiainjectedsourceget_objectfilename"></a>IDiaInjectedSource::get_objectFilename
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Pobiera nazwę pliku obiektu, do którego zostało skompilowane źródło.  
  
## <a name="syntax"></a>Składnia  
  
```cpp#  
HRESULT get_objectFilename (   
   BSTR* pRetVal  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pRetVal`  
 określoną Zwraca nazwę pliku obiektu, do którego zostało skompilowane źródło.  
  
## <a name="return-value"></a>Wartość zwracana  
 Jeśli powiedzie się, zwraca `S_OK` . Zwraca wartość, `S_FALSE` Jeśli ta właściwość nie jest obsługiwana. W przeciwnym razie zwraca kod błędu.  
  
## <a name="see-also"></a>Zobacz też  
 [IDiaInjectedSource](../../debugger/debug-interface-access/idiainjectedsource.md)
