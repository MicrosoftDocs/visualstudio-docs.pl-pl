---
title: 'IDebugApplication:: AddStackFrameSniffer | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugApplication.AddStackFrameSniffer
apilocation:
- pdm.dll
helpviewer_keywords:
- IDebugApplication::AddStackFrameSniffer
ms.assetid: a7a9684a-14c5-415a-ae63-a17397d58d07
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: a461c24b6f62f1e0ece88915e097faf0c59f15e7
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2019
ms.locfileid: "72575033"
---
# <a name="idebugapplicationaddstackframesniffer"></a>IDebugApplication::AddStackFrameSniffer
Dodaje do tej aplikacji dostawcę modułu wyliczającego ramki stosu.  
  
## <a name="syntax"></a>Składnia  
  
```cpp
HRESULT AddStackFrameSniffer(  
   IDebugStackFrameSniffer*  pdsfs,  
   DWORD*                    pdwCookie  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pdsfs`  
 podczas Dostawca modułu wyliczającego ramki stosu, który ma zostać dodany do tej aplikacji.  
  
 `pdwCookie`  
 określoną Plik cookie służący do usuwania tego dostawcy modułu wyliczającego ramki stosu z aplikacji.  
  
## <a name="return-value"></a>Wartość zwracana  
 Metoda zwraca `HRESULT`. Przykładowe dopuszczalne wartości wymieniono w tabeli poniżej.  
  
|Wartość|Opis|  
|-----------|-----------------|  
|`S_OK`|Wykonanie metody powiodło się.|  
  
## <a name="remarks"></a>Uwagi  
 Mimo że aparaty języka zwykle wywołują tę metodę, aby uwidocznić ramki stosu do debugera, możliwe jest, aby inne jednostki uwidaczniali ramki stosu.  
  
## <a name="see-also"></a>Zobacz także  
 [IDebugApplication   interfejsu](../../winscript/reference/idebugapplication-interface.md)  
 [IDebugApplication:: RemoveStackFrameSniffer](../../winscript/reference/idebugapplication-removestackframesniffer.md)    
 [IDebugStackFrameSniffer, interfejs](../../winscript/reference/idebugstackframesniffer-interface.md)