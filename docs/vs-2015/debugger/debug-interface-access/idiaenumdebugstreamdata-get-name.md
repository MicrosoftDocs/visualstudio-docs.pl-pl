---
title: IDiaEnumDebugStreamData::get_name | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumDebugStreamData::get_Name method
ms.assetid: e6cf2bed-ee2b-4122-886d-c20d93df7ff2
caps.latest.revision: 10
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 71dc914ef76c512605dbef75de04781459c4929d
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54775803"
---
# <a name="idiaenumdebugstreamdatagetname"></a>IDiaEnumDebugStreamData::get_name
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Pobiera nazwę strumienia danych debugowania.  
  
## <a name="syntax"></a>Składnia  
  
```cpp#  
HRESULT get_Name (   
   BSTR * pRetVal  
)  
```  
  
#### <a name="parameters"></a>Parametry  
 pRetVal  
 [out] Zwraca nazwę strumienia danych debugowania.  
  
## <a name="return-value"></a>Wartość zwracana  
 Jeśli operacja się powiedzie, zwraca `S_OK`; w przeciwnym razie zwraca kod błędu.  
  
## <a name="see-also"></a>Zobacz też  
 [IDiaEnumDebugStreamData](../../debugger/debug-interface-access/idiaenumdebugstreamdata.md)
