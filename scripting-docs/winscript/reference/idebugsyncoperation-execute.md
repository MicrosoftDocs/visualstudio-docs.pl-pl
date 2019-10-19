---
title: 'IDebugSyncOperation:: Execute | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugSyncOperation.Execute
apilocation:
- jscript.dll
helpviewer_keywords:
- IDebugSyncOperation::Execute
ms.assetid: a45b8c7d-c51a-4098-877f-fbec2f1f6947
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 25da02e6736cc2f8ac27c82f922bd515e791bef1
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2019
ms.locfileid: "72576695"
---
# <a name="idebugsyncoperationexecute"></a>IDebugSyncOperation::Execute
Synchronicznie wykonuje operację i zwraca wartość.  
  
## <a name="syntax"></a>Składnia  
  
```cpp
HRESULT Execute(  
   IUnknown**  ppunkResult  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `ppunkResult`  
 określoną Parametr obiektu zwrócony przez operację.  
  
## <a name="return-value"></a>Wartość zwracana  
 Metoda zwraca `HRESULT`. Przykładowe dopuszczalne wartości wymieniono w tabeli poniżej.  
  
|Wartość|Opis|  
|-----------|-----------------|  
|`S_OK`|Wykonanie metody powiodło się.|  
|`E_ABORT`|Operacja została przerwana przez wywołanie metody `IDebugSyncOperation::InProgressAbort`.|  
  
## <a name="remarks"></a>Uwagi  
 Menedżer debugowania procesów w wątku docelowym wywołuje metodę `Execute` synchronicznie.  
  
## <a name="see-also"></a>Zobacz także  
 [IDebugSyncOperation, interfejs](../../winscript/reference/idebugsyncoperation-interface.md)