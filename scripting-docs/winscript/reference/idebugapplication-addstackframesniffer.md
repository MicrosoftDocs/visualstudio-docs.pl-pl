---
title: IDebugApplication::AddStackFrameSniffer | Microsoft Docs
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
ms.openlocfilehash: 16fb941a91482c548284dc3d4317a472fd9be641
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62991051"
---
# <a name="idebugapplicationaddstackframesniffer"></a>IDebugApplication::AddStackFrameSniffer
Dodaje dostawcę moduł wyliczający ramek stosu do tej aplikacji.  
  
## <a name="syntax"></a>Składnia  
  
```cpp
HRESULT AddStackFrameSniffer(  
   IDebugStackFrameSniffer*  pdsfs,  
   DWORD*                    pdwCookie  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pdsfs`  
 [in] Dostawca modułu wyliczającego ramki stosu do dodania do tej aplikacji.  
  
 `pdwCookie`  
 [out] Plik cookie, który służy do usuwania tego dostawcy moduł wyliczający ramek stosu z aplikacji.  
  
## <a name="return-value"></a>Wartość zwracana  
 Metoda ta zwraca `HRESULT`. Przykładowe dopuszczalne wartości wymieniono w tabeli poniżej.  
  
|Wartość|Opis|  
|-----------|-----------------|  
|`S_OK`|Wykonanie metody powiodło się.|  
  
## <a name="remarks"></a>Uwagi  
 Aparaty języka zwykle wywołują tę metodę w celu udostępnienia ich ramek stosu do debugera, może się jednak zdarzyć na inne jednostki do udostępnienia ramki stosu.  
  
## <a name="see-also"></a>Zobacz też  
 [Interfejs IDebugApplication](../../winscript/reference/idebugapplication-interface.md)   
 [IDebugApplication::RemoveStackFrameSniffer](../../winscript/reference/idebugapplication-removestackframesniffer.md)   
 [IDebugStackFrameSniffer, interfejs](../../winscript/reference/idebugstackframesniffer-interface.md)