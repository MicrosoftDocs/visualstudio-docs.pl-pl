---
title: IDebugSyncOperation::Execute | Dokumentacja firmy Microsoft
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
ms.openlocfilehash: a2bc204169ff94a240e363eb8caa35ec8c7de9be
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "63004877"
---
# <a name="idebugsyncoperationexecute"></a>IDebugSyncOperation::Execute
Synchronicznie wykonuje operację i zwraca.  
  
## <a name="syntax"></a>Składnia  
  
```cpp
HRESULT Execute(  
   IUnknown**  ppunkResult  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `ppunkResult`  
 [out] Parametr obiekt zwrócony przez operację.  
  
## <a name="return-value"></a>Wartość zwracana  
 Metoda ta zwraca `HRESULT`. Przykładowe dopuszczalne wartości wymieniono w tabeli poniżej.  
  
|Wartość|Opis|  
|-----------|-----------------|  
|`S_OK`|Wykonanie metody powiodło się.|  
|`E_ABORT`|Operacja została przerwana, przez wywołanie metody `IDebugSyncOperation::InProgressAbort` metody.|  
  
## <a name="remarks"></a>Uwagi  
 Menedżer debugowania procesów w wywołaniach wątek docelowy `Execute` metoda synchronicznie.  
  
## <a name="see-also"></a>Zobacz też  
 [IDebugSyncOperation, interfejs](../../winscript/reference/idebugsyncoperation-interface.md)