---
title: 'IDebugAsyncOperation:: Start | Microsoft Docs'
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
ms.openlocfilehash: 485eb34ebe200e7f7898d9338effed37cbf2aa10
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2019
ms.locfileid: "72573245"
---
# <a name="idebugasyncoperationstart"></a>IDebugAsyncOperation::Start
Powoduje rozpoczęcie operacji asynchronicznej.  
  
## <a name="syntax"></a>Składnia  
  
```cpp
HRESULT Start(  
   IDebugAsyncOperationCallBack*  padocb  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `padocb`  
 Interfejs wywołania zwrotnego, który odbiera zdarzenia stanu z tej operacji.  
  
## <a name="return-value"></a>Wartość zwrócona  
 Metoda zwraca `HRESULT`. Przykładowe dopuszczalne wartości wymieniono w tabeli poniżej.  
  
|Value|Opis|  
|-----------|-----------------|  
|`S_OK`|Wykonanie metody powiodło się.|  
|`E_UNEXPECTED`|Operacja jest już w stanie oczekiwania.|  
  
## <a name="remarks"></a>Uwagi  
 Ta metoda powoduje, że `IDebugSyncOperation::Execute` być wywoływana asynchronicznie w wątku uzyskanym z `IDebugSyncOperation::GetTargetThread`. Ta metoda powinna być wywoływana tylko z poziomu wątku debugera; w przeciwnym razie nie będzie zwracana do momentu ukończenia operacji.  
  
## <a name="see-also"></a>Zobacz także  
 [IDebugAsyncOperation:: Abort](../../winscript/reference/idebugasyncoperation-abort.md)   
 [IDebugAsyncOperation  interfejsu](../../winscript/reference/idebugasyncoperation-interface.md)  
 [IDebugSyncOperation:: Execute](../../winscript/reference/idebugsyncoperation-execute.md)   
 [IDebugSyncOperation::GetTargetThread](../../winscript/reference/idebugsyncoperation-gettargetthread.md)