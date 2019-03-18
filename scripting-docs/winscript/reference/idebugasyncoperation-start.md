---
title: IDebugAsyncOperation::Start | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugAsyncOperation.Start
apilocation:
- pdm.dll
helpviewer_keywords:
- IDebugAsyncOperation::Start
ms.assetid: a7272364-28e0-48ae-8405-b8bce8a6b9fd
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: b3e02869abab65878412f96b77d5782b9717a1b6
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2019
ms.locfileid: "58155709"
---
# <a name="idebugasyncoperationstart"></a>IDebugAsyncOperation::Start
Powoduje, że operacja asynchroniczna rozpocząć.  
  
## <a name="syntax"></a>Składnia  
  
```cpp
HRESULT Start(  
   IDebugAsyncOperationCallBack*  padocb  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `padocb`  
 Interfejs wywołania zwrotnego, który odbiera zdarzenia stanu z tej operacji.  
  
## <a name="return-value"></a>Wartość zwracana  
 Metoda ta zwraca `HRESULT`. Przykładowe dopuszczalne wartości wymieniono w tabeli poniżej.  
  
|Wartość|Opis|  
|-----------|-----------------|  
|`S_OK`|Wykonanie metody powiodło się.|  
|`E_UNEXPECTED`|Operacja jest już oczekujące.|  
  
## <a name="remarks"></a>Uwagi  
 Ta metoda powoduje `IDebugSyncOperation::Execute` ma zostać wywołana asynchronicznie w wątku uzyskany z `IDebugSyncOperation::GetTargetThread`. Ta metoda powinna być wywoływana tylko z w wątku debuger; w przeciwnym razie nie zostanie zwrócone do czasu ukończenia operacji.  
  
## <a name="see-also"></a>Zobacz też  
 [IDebugAsyncOperation::Abort](../../winscript/reference/idebugasyncoperation-abort.md)   
 [Interfejs IDebugAsyncOperation](../../winscript/reference/idebugasyncoperation-interface.md)   
 [IDebugSyncOperation::Execute](../../winscript/reference/idebugsyncoperation-execute.md)   
 [IDebugSyncOperation::GetTargetThread](../../winscript/reference/idebugsyncoperation-gettargetthread.md)