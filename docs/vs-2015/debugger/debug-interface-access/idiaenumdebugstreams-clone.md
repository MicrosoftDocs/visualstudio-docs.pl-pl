---
title: 'IDiaEnumDebugStreams:: Clone | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumDebugStreams::Clone method
ms.assetid: e85ec592-de97-4f95-a774-1623315ba415
caps.latest.revision: 11
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: f5a93d411a5edc8d52c54f374fb221a9122fc12a
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "68187371"
---
# <a name="idiaenumdebugstreamsclone"></a>IDiaEnumDebugStreams::Clone
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Tworzy moduł wyliczający, który zawiera ten sam stan wyliczania co bieżący moduł wyliczający.  
  
## <a name="syntax"></a>Składnia  
  
```cpp#  
HRESULT Clone (   
   IDiaEnumDebugStreams** ppenum  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `ppenum`  
 określoną Zwraca obiekt [IDiaEnumDebugStreams](../../debugger/debug-interface-access/idiaenumdebugstreams.md) , który zawiera duplikat modułu wyliczającego. Strumienie nie są duplikowane, tylko moduł wyliczający.  
  
## <a name="return-value"></a>Wartość zwracana  
 Jeśli powiedzie się, zwraca `S_OK` ; w przeciwnym razie zwraca kod błędu.  
  
## <a name="see-also"></a>Zobacz też  
 [IDiaEnumDebugStreams](../../debugger/debug-interface-access/idiaenumdebugstreams.md)
