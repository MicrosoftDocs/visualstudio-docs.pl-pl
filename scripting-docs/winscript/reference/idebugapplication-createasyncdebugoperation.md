---
title: IDebugApplication::CreateAsyncDebugOperation | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugApplication.CreateAsyncDebugOperation
apilocation:
- pdm.dll
helpviewer_keywords:
- IDebugApplication::CreateAsyncDebugOperation
ms.assetid: bc32b101-6364-4498-8458-bd5f3ab5ad94
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: c60c84dbd3be9248e2bd075e65d53f7f9361d0b5
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62991016"
---
# <a name="idebugapplicationcreateasyncdebugoperation"></a>IDebugApplication::CreateAsyncDebugOperation
Zapewnia dostęp asynchronicznych operacji danego synchroniczne debugowania.  
  
## <a name="syntax"></a>Składnia  
  
```cpp
HRESULT CreateAsyncDebugOperation(  
   IDebugSyncOperation*    psdo,  
   IDebugAsyncOperation**  ppado  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `psdo`  
 [in] Obiekt operacji synchronicznych debugowania.  
  
 `ppado`  
 [out] Obiekt operacji debugowania asynchronicznego.  
  
## <a name="return-value"></a>Wartość zwracana  
 Metoda ta zwraca `HRESULT`. Przykładowe dopuszczalne wartości wymieniono w tabeli poniżej.  
  
|Wartość|Opis|  
|-----------|-----------------|  
|`S_OK`|Wykonanie metody powiodło się.|  
  
## <a name="remarks"></a>Uwagi  
 Ta metoda umożliwia silników języka asynchronicznie obliczać wyrażeń bez jawnie synchronizacji z wątkiem w debugerze. Aby uzyskać więcej informacji, zobacz [interfejs IDebugSyncOperation](../../winscript/reference/idebugsyncoperation-interface.md) i [interfejs IDebugAsyncOperation](../../winscript/reference/idebugasyncoperation-interface.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Interfejs IDebugApplication](../../winscript/reference/idebugapplication-interface.md)   
 [Interfejs IDebugSyncOperation](../../winscript/reference/idebugsyncoperation-interface.md)   
 [IDebugAsyncOperation, interfejs](../../winscript/reference/idebugasyncoperation-interface.md)