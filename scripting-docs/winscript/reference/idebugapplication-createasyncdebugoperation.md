---
title: 'IDebugApplication:: CreateAsyncDebugOperation | Microsoft Docs'
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
ms.openlocfilehash: 1feb8207fb7e7a7faf4427be189c4952139ef32c
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2019
ms.locfileid: "72575556"
---
# <a name="idebugapplicationcreateasyncdebugoperation"></a>IDebugApplication::CreateAsyncDebugOperation
Zapewnia asynchroniczny dostęp do danej operacji debugowania synchronicznego.  
  
## <a name="syntax"></a>Składnia  
  
```cpp
HRESULT CreateAsyncDebugOperation(  
   IDebugSyncOperation*    psdo,  
   IDebugAsyncOperation**  ppado  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `psdo`  
 podczas Synchroniczny obiekt operacji debugowania.  
  
 `ppado`  
 określoną Asynchroniczny obiekt operacji debugowania.  
  
## <a name="return-value"></a>Wartość zwracana  
 Metoda zwraca `HRESULT`. Przykładowe dopuszczalne wartości wymieniono w tabeli poniżej.  
  
|Wartość|Opis|  
|-----------|-----------------|  
|`S_OK`|Wykonanie metody powiodło się.|  
  
## <a name="remarks"></a>Uwagi  
 Ta metoda umożliwia aparatom języka obliczanie wyrażeń asynchronicznie bez jawnego synchronizowania z wątkiem debugera. Aby uzyskać więcej informacji, zobacz [interfejs IDebugSyncOperation](../../winscript/reference/idebugsyncoperation-interface.md) i [interfejs IDebugAsyncOperation](../../winscript/reference/idebugasyncoperation-interface.md).  
  
## <a name="see-also"></a>Zobacz także  
 [IDebugApplication   interfejsu](../../winscript/reference/idebugapplication-interface.md)  
 [IDebugSyncOperation   interfejsu](../../winscript/reference/idebugsyncoperation-interface.md)  
 [IDebugAsyncOperation, interfejs](../../winscript/reference/idebugasyncoperation-interface.md)